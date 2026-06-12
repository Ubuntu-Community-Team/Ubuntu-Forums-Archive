---
title: "Help with PHP"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by wewantutopia on 2009-12-29
Ok, lets try this again.  I had created this post yesterday: [http://ubuntuforums.org/showthread.php?p=8572345#post8572345](http://ubuntuforums.org/showthread.php?p=8572345#post8572345) but I guess I didn't know exactly the right questions to ask.  

I've got apache etc working correctly, have wordpress and jinzora working.  I learned that if I throw a folder (or link) in the /var/www/ folder the contents would then be accessible for stream/download.  This is awesome, however I would like it password protected.  

I am a coding noob.  I know some BASIC and can *kind of* read some other code.  I started with a simple HTML code with a java script but learned that java has the potential for allowing malicious script.  I've scrapped that.  I'm now working with PHP.  This is what I have so far,  called it index.php:
> <?php

// Define your username and password

$username = "me";

$password = "you";


if ($_POST['txtUsername'] != $username || $_POST['txtPassword'] != $password) {

?>

<html>
<body bgcolor="#CCFFBB"></body>
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<h1><center>Login</center></h1>

<br /><form name="form" method="post" action="<?php echo $_SERVER['PHP_SELF']; ?>">

    <center><p><label for="txtUsername">Username:</label>

    <br /><input type="text" title="Enter your Username" name="txtUsername" /></p></center>

    <center><p><label for="txtpassword">Password:</label>

    <br /><input type="password" title="Enter your password" name="txtPassword" /></p></center>


    <br /><center><p><input type="submit" name="Submit" value="Login" /></p></center>

</form>


<?php

}

else {

?>

<p>This is the protected page. Your private content goes here.</p>

<?php

echo getcwd();

}

?> 
Most of this I found on a website with some minor editing by me.  Would I would like to happen after the correct username/password has been entered is for it to enter the folder like the index.php is not there.  Is this possible?  If so, what steps would I need to take?  Thank you!!!!!!!!!!!!

---

### Post by kevinatkins on 2009-12-29
Hi,

From what you've written, what I think you want to accomplish is to 'password protect' your documents on your webserver (ie, within the document root of your webserver).

If that's the case, you don't need to concern yourself with PHP - Apache can handle this for you, using user authentication. This can be set up either within the main Apache configuration file, or using a special .htaccess file that you drop into the directory you want to protect.

For more information, look here -

[http://httpd.apache.org/docs/2.2/howto/htaccess.html](http://httpd.apache.org/docs/2.2/howto/htaccess.html)

The upshot is, when a user attempts to browse a protected site / folder, a browser pop-up will appear, asking for username / password credentials.

This is an easier, and better way of accomplishing what you want than using PHP, unless you're building a complete PHP site (which might thereby involve database connectivity, etc)

---

### Post by spikyjt on 2009-12-29
Apache security is of course the right choice if you are building a simple custom site. But you mention you already have Wordpress installed. If the content you wish to protect is in or could be in wordpress, why not use the password protect function in WP? This will be simpler for you to setup. It's worth learning Apache config and PHP, but it a long road, so you might be better off using what's readily available to you, to get the functions you need now, and testing out other setups for later. Also if you need a user friendly way to configure your server, try [Webmin]("http://webmin.com/")

---

### Post by wewantutopia on 2009-12-29
Thank you both for your help.  I am currently reading the .htaccess link.  Since I learned you can access anything you put in /var/www/ i created a files folder and added links to my music/movies folders for web access (using DynDNS).  Just trying to protect my media from being shared with the world. (i guess that's illegal)

---

### Post by wewantutopia on 2009-12-30
Figured it out using this AWESOME script!!!

[http://autoindex.sourceforge.net/](http://autoindex.sourceforge.net/)

Just what I was looking for!  
Just decompressed it, dropped it's contents in a new file in my /var/www/ folder and when I accessed the page via browser a config screen came up and thats it!  Then in a new folder with this folder added the links to my media and viola!

Thanks for the help.


(script allows for uploading too if you allow it.  You can set the user level [guest, user, mod, admin] of who gets to upload...awesome!)

---

