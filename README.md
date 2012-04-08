# FormIT automagical forms #

FormIT “automagically” creates, validates and renders beautifull HTML forms based on your PHPActiveRecord, Yii AR or Doctrine application model.

## How the magic works? ##

FormIT will detect your model attributes types and it will try to recognize the most suitable HTML inputs (of course, you can change that as you wish) and basic validations like not empty, string length and numeric ranges, dates, relationships, etc.

## Requirements ##

Requirements:

- PHP 5.3+ (because some of the supported AR/ORM libraries need it)
- Some AR/ORM library. 

We currently support:

- Yii Framework 1.1

We plan to support:

- PHPActiveRecord
- Zend Framework 1.1./2 (Zend_DbTable's)
- Doctrine 2

## License ##

PUT THE LICENSE HEREEE (STILL DEFINING)

## Using FormIT ##

### Installing ###

First you need to require the library base file, like:

    require 'library/stuff/ohBoy/FormIT/FormIT.php';

Then you can change the default settings inside your application PHP config file (not necessary if you are okay with the default settings):

    <?php
    FormIT::config(array(
        'adapter'   => FormIT::ADAPTER_YII // FormIT Adapter. For now, only Yii Framework
        'flags'     => array("No", "Yes") // Default flags for boolean/tinyint fields
        'flagsHtml' => FormIT::HTML_INPUT_RADIO // Default HTML tag for flags (could be radio, checkbox or select)
    ));
    ?>

About other options see “Advanced config” bellow.

### Basic usage ###

Just “echo” your model FormIT:

    <?php echo new FormIT($modelClass); ?>

It will detect all of your model attributes types and use the most suitable HTML form tags for each one.

### Tag blocks ###

If you want to explicitly define each tag type:

    <?php
    $form = new FormIT($modelClass);

    echo $form->start();
    
    // Will generate <input type="text" />
    echo $form->text(array('name', 'email', 'cat_name'));

    // Will generate <input type="radio" />
    echo $form->radio(array('sex','has_more_than_one_cat'));

    // Will generate submit and reset buttons (default)
    echo $form->buttons;
    
    echo $form->end();
    ?>

## Advanced config ##

LIST HERE ALL THE ADVANCED SETTINGS