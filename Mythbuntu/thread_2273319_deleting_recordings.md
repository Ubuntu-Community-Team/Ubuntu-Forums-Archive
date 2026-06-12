---
title: "deleting recordings"
date: 2015-04-12
forum: Mythbuntu
---

### Post by deanie44 on 2015-04-12
Hi everyone.  I have 106  recordings of mike & molly in the directory. but only 57 in the mythtv database.  How do I tell which recordings can be deleted?  I tried using mythlink.pl, but you cannot use it on one directory.  It does the entire database.  Is there anyway that I can found out which recording are deletable?  Any help will be appreciated.  deanie44

---

### Post by khPWXxF on 2015-04-12
Have you tried find_orphans?
[https://www.mythtv.org/wiki/Find_orphans.py](https://www.mythtv.org/wiki/Find_orphans.py)
Phil

---

### Post by GreatBeach on 2015-04-15
Hey Deanie, I'll take a stab at it..  :)

I put together a script that will identify recorded files in a directory that are not in the MythTV database.    You can even have the script remove the files if you want.     Right now this script will just show you the recordings not in the database.      If you want to give it a try, copy the code to a text file, change the user settings items, save and then set the executable flag (chmod +x <filename>)... then run it.

```

#!/usr/bin/php
<?php  // identifies files in a directory but not in the MythTV database

//User settings..
$myth_recordings_path = "/var/lib/mythtv/recordings/";
$mythtv_database_pass = "hi-mom";
$video_file_extention = "mpg";

//connect to the MythTV database
$db = new mysqli('localhost', 'mythtv', $mythtv_database_pass,'mythconverg');
if($db->connect_errno > 0) die('Unable to connect to database [' . $db->connect_error . ']');

//loop through the recording directory and see if there is a match in the DB
if ($handle = opendir($myth_recordings_path)) {
    while (false !== ($file = readdir($handle))) {

        if (($file === '.') || ($file === '..')) continue;

        $file_ext = pathinfo($file, PATHINFO_EXTENSION);
        if ($video_file_extention == $file_ext) {
                        
            $sql = "SELECT * FROM `recorded` WHERE `basename` = '" . $file . "'";
            if (!$result = $db->query($sql)) die('There was an error running the query [' . $db->error . ']');        
            $rows = $result->num_rows;
            
            if ($rows == 0) {
                echo $file . " is not found in the MythTV database...\n";
                //uncomment the following to delete files not found in the MythTV database
                //unlink($myth_recordings_path . $file);
                //unlink($myth_recordings_path . $file . ".-1.100x75.png");
                //unlink($myth_recordings_path . $file . ".png");
            }
            
            $result->free();
        }

    }
    closedir($handle);
}
$db->close();
?>

```

---

### Post by deanie44 on 2015-05-06
Hi GreatBeach.  Thanks for answering my post.  I copied the script to gedit and named it "deletedrecordings.  I tried to run it with chmod +x, but I get an error message stating that there is no such file or directory.  Any help will be appreciated.  deanie44

---

### Post by elliott6 on 2015-05-20
deanie,

Did you make any changes to the code? From the script, it's listed as user preferences at the top - 

//User settings..
$myth_recordings_path = "/var/lib/mythtv/recordings/";
$mythtv_database_pass = "hi-mom";
$video_file_extention = "mpg";

You would want to tweak the above to "fit" your settings. For example, I have my recordings, videos, music, etc. in a different directory than the default. Therefore, I would need to change $myth_recordings_path = to my directory, which would look like this - 

//User settings..
$myth_recordings_path = "**/media/recordings/**";

Same goes for password, etc. So change as you see fit if you have made modifications, else post back and we can try to sort it out.

Good luck!

elliott

---

### Post by deanie44 on 2015-05-23
Hi GreatBeach and elliott6.  Thank you for answering my post.  I have plugged in the correct info in the script, but is the file extension .php?  How am I to execute it?  I tried to run it, but it did not work.  I receive an error message saying that the command is not found.  I know nothing about executing scripts.  I need help.  deanie44

---

### Post by khPWXxF on 2015-05-25
The 'standard' script is find_orphans and that is one that everyone uses in this situation.  Did you try it?

[https://www.mythtv.org/wiki/Find_orphans.py](https://www.mythtv.org/wiki/Find_orphans.py)

Phil

---

### Post by deanie44 on 2015-05-25
Thanks  				 				 					 						 	[**[COLOR=#000000]khPWXxF[/COLOR]**]("http://ubuntuforums.org/member.php?u=1844453") for answering my post.  I have tried Find_orphans, but it does not delete the files in the directory. deanie44

---

### Post by khPWXxF on 2015-05-26
Do you mean that it identified them but failed trying to delete them?
Permissions?
Phil

---

### Post by deanie44 on 2015-06-01
Phil, thank you for answering my post.  find_orphans. py will identify the recordings, but will not delete them in the recordings directory in mythtv(/var/lib/mythtv/recordings).  I takes forever to delete the bad recordings it found in the database.  I left the terminal open running find_orphans.py for two hours and no recordings was deleted.  Is there another way to delete the recordings?  deanie44

---

### Post by khPWXxF on 2015-06-01
Yes, it can be rather sluggish and you need to give it time.  Did the number of spurious recording change at a subsequent run?  If so then it  is working.

Your backend is running at the time?
You are running on the same system as the backend?
Your spurious recordings are also on that system?

What are the permissions on the directory?  
```
ls -l /var/lib/mythtv/recordings/
```
and on sample recordings?f
```
ls -l /var/lib/mythtv/recordings/*.mpg
```
Phil

---

