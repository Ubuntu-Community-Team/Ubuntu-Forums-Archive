---
title: "Apache2 Upload Form?"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by django0909 on 2009-07-18
Hi all,

I have a bit of a problem with my apache2 installation.

I'm only using it locally at the moment and I have a server installation up and running, using the httpd.conf file to point at my music folder. This folder is password protected using .htaccess/.htpasswd - all of this works fine and I'm quite happy.

What I want to be able to do now is have users who log on to my server be directed to a simple form, whereby they can browse the root directory of my server or upload data to a seperate folder within my server.

I have some vague ideas but don't really know where to start!

Can someone advise/help?

Cheers,

-django

---

### Post by wojox on 2009-07-18
Did you install php?
This can easily be done with php.

---

### Post by django0909 on 2009-07-18
I figured php would be the way to go yes. 

I'll give it a go. I'm not asking to be handed this one on a plate at all but if anyone has a simple script kicking around that could do the job - would be appreciated!

-django

---

### Post by django0909 on 2009-07-18
OK - I am but no means a php expert but have done the following.

1. Created an html document in the root of my server, with the following code.

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html><head></head><body>Welcome to Dan's PC.<br><br>Browse <a href="/Music">here</a>, or upload below.<br><br><br><form enctype="multipart/form-data" action="uploader.php" method="post">
<input name="MAX_FILE_SIZE" value="100000" type="hidden">
Choose a file to upload: <input name="uploadedfile" type="file"><br>
<input value="Upload File" type="submit">
</form>
</body></html>
```

2. Pinched a quick php script to deal with the uploading process, (uploader.php), and put this in the root directory of my server also. That script looks like this:

```
<?
$target_path = "uploads";

/* Add the original filename to our target path.  
Result is "uploads/filename.extension" */
$target_path = $target_path . basename( $_FILES['uploadedfile']['name']); 

$target_path = "uploads";

$target_path = $target_path . basename( $_FILES['uploadedfile']['name']); 

if(move_uploaded_file($_FILES['uploadedfile']['tmp_name'], $target_path)) {
    echo "The file ".  basename( $_FILES['uploadedfile']['name']). 
    " has been uploaded";
} else{
    echo "There was an error uploading the file, please try again!";
}
?>

```

3. Created a folder called 'uploads' in the root dir of my server.

And that is all. But as I said, I'm by no means a php pro and can't work out why it keeps returning me an error :(

Can anyone give me any pointers? Would be most grateful!

-django

---

### Post by wojox on 2009-07-18
What's the error?

echo "There was an error uploading the file, please try again!";

---

### Post by django0909 on 2009-07-18
Yeah, that's the one!

---

### Post by wojox on 2009-07-18
Try:

```
<?
$target_path = "uploads/";

/* Add the original filename to our target path.  
Result is "uploads/filename.extension" */
$target_path = $target_path . basename( $_FILES['uploadedfile']['name']); 

if(move_uploaded_file($_FILES['uploadedfile']['tmp_name'], $target_path)) {
    echo "The file ".  basename( $_FILES['uploadedfile']['name']). 
    " has been uploaded";
} else{
    echo "There was an error uploading the file, please try again!";
}
?>
```

---

### Post by django0909 on 2009-07-18
Thanks for the attempt but it still returns the same. Any other ideas?

---

### Post by wojox on 2009-07-18
```
<form enctype="multipart/form-data" action="upload.php" method="POST">
    <input type="hidden" name="MAX_FILE_SIZE" value="512000" />
    Send this file: <input name="userfile" type="file" />
    <input type="submit" value="Send File" />
</form>
```

Next, the php to accept the file, upload.php

```
<?php

$uploaddir = '/var/www/uploads/';
$uploadfile = $uploaddir . basename($_FILES['userfile']['name']);

echo "<p>";

if (move_uploaded_file($_FILES['userfile']['tmp_name'], $uploadfile)) {
  echo "File is valid, and was successfully uploaded.\n";
} else {
   echo "Upload failed";
}

echo "</p>";
echo '<pre>';
echo 'Here is some more debugging info:';
print_r($_FILES);
print "</pre>";

?> 

```

---

### Post by HyperHacker on 2009-07-18
Check the error code:```
if($_FILES['file']['error'] > 0)
	echo 'Upload failed: error ' . $_FILES['file']['error'] . '<br />';
```I'm not sure how to get the meaning of those errors, but it might tell you what's going on.

---

### Post by django0909 on 2009-07-18
Hi guys,

Thanks for your help so far - I'm getting somewhere now!

The code wojox gave me returns the following:

> Warning: move_uploaded_file(/home/dan/Desktop/Music/Music/uploads/lloydsmay.jpg) [function.move-uploaded-file]: failed to open stream: Permission denied in /home/dan/Desktop/Music/upload.php on line 8

Warning: move_uploaded_file() [function.move-uploaded-file]: Unable to move '/tmp/phpl8zcEs' to '/home/dan/Desktop/Music/Music/uploads/lloydsmay.jpg' in /home/dan/Desktop/Music/upload.php on line 8
Upload failed

Here is some more debugging info:Array
(
    [userfile] => Array
        (
            [name] => lloydsmay.jpg
            [type] => image/jpeg
            [tmp_name] => /tmp/phpl8zcEs
            [error] => 0
            [size] => 381696
        )

)


Do I need to chmod something to sort the permissions problem? If so - what? And what do I chmod it do?

Thanks for all your help so far!

-django

---

### Post by django0909 on 2009-07-18
Fixed my own problem, thanks for your help all!

---

