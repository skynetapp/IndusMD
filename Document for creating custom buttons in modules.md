###### Author       : Sri Sai Venkatesh.
###### Date          : 26-February-2013
###### Description: This document comprise of total flow of Creating custom buttons in the modules.
###### Team         : EMR Team.
###### SugarCRM version : 6.5

## Aim
This document explains the process of creating custom buttons in the Meetings module detail view.

#### Step 1 
``` Go to <root>\custom\modules\Meetings\metadata\detailviewdefs.php ```
#### Step 2
 In this file we have an array of buttons defined as follows
``` 
array (
 'buttons' =>
    array (
      0 => 'EDIT', 
      1 => 'DUPLICATE',
    )
```
#### Step 3
To add a custom button, we need to add another array element with its key as
customCode as follows
``` 
    2 => 'DELETE',
    3 => array ('customCode' => '<input title="Post Meeting" id= "phs"class="button" type="button" onclick="MM_openBrWindow(\'index.php?entryPoint=PostMeeting&record={$fields.id.value}\',\'\',\'toolbar=no,location=no,status=no,menubar=yes,scrollbars=yes,resizable=yes,width=800,height=400,top=200,left=400\')" name="Post" widht="80" value="Post Meeting">',     
        ), 
```
#### Step 4
The path of the entry point in above code should be defined in entry_point_registry.php
file which is located in <root>\include\mvc\controller.

#### Step 5
 Here the definition of entry point should be as:            
``` 
'PostTo'=>array('file'=>'MangoLib/custom/modules/Meetings/postMeeting.php','auth'=>true), 
```
*Note: Here entry path can be any thing accessable with in sugarcrm structure.*
#### Step 6
In the php file (/postMeeting.php) of entrypoint the code to perform action on click of the 
button should be defined. 
