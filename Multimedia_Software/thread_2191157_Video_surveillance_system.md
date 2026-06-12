---
title: "Video surveillance system"
date: 2013-12-01
forum: Multimedia Software
---

### Post by Stjepan225 on 2013-12-01
I have security camera connected on usb video grabber (easycap). Drivers are successfully installed. I have configured motion program and  mencoder TV capture and they are working fine, so i have motion detection and also program for manual recording. Problem is that both programs won't work together. There is program called ZoneMinder, but it's not working on my kubuntu. I tried to configure it but it didn't work.


I need motion detection and video recording at the same time. Is there any program or can someone show me detailed instructions how to setup ZoneMinder?


Thanks!
[ATTACH=CONFIG]248223[/ATTACH]

---

### Post by rackit on 2013-12-02
Here is a great place to start: [http://www.zoneminder.com/wiki/index.php/Ubuntu](http://www.zoneminder.com/wiki/index.php/Ubuntu) they have ubuntu specific guides.

---

### Post by Stjepan225 on 2013-12-09
> **rackit said:**
> Here is a great place to start: [http://www.zoneminder.com/wiki/index.php/Ubuntu](http://www.zoneminder.com/wiki/index.php/Ubuntu) they have ubuntu specific guides.

Nope, it's not working. I tried it all by the instructions. I have Kubuntu 13.10 x64. I also tried this tutorial: [install zoneminder (1.25) on ubuntu (12.04)]("http://janhellevik.com/?p=1045")

When i type this: [https://server/zm](https://server/zm)          i get this message: This webpage is not available

[http://localhost/zm](http://localhost/zm) i get this: [h=1]Not Found[/h][COLOR=#000000][FONT=Times New Roman]The requested URL /zm was not found on this server.[/FONT][/COLOR]

When i had kubuntu 13.04 i successfully installed zoneminder and i managed to access that page. But in configuration i couldn't get working v4l2, there was no video and camera status line was red. 

Any help from people with better experience? Thanks!

---

### Post by rackit on 2013-12-09
Is apache working? If so, we'll have to look at your apache config as it relates to ZM.

---

### Post by Stjepan225 on 2013-12-10
Here is the image of konsole:

---

### Post by Stjepan225 on 2013-12-10
When i open localhost page in chrome i get this message:

**It works!**

[COLOR=#000000][FONT=Times New Roman]This is the default web page for this server.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]The web server software is running but no content has been added, yet.


Edit:
I found this- [/FONT][/COLOR][SIZE=2][COLOR=#2C2C29][FONT=Tahoma]Additional info for Ubuntu 13.10[/FONT][/COLOR][/SIZE][COLOR=#2C2C29][FONT=Tahoma][SIZE=2]Apparently, you must now link the file as follows:[/SIZE][/FONT][/COLOR]
[COLOR=#2C2C29][FONT=Tahoma][SIZE=2]sudo ln -s /etc/zm/apache.conf /etc/apache2/conf-available/zoneminder.conf[/SIZE][/FONT][/COLOR]
[COLOR=#2C2C29][FONT=Tahoma][SIZE=2]&#8230;then enable it&#8230;[/SIZE][/FONT][/COLOR]
[COLOR=#2C2C29][FONT=Tahoma][SIZE=2]sudo a2enconf zoneminder[/SIZE][/FONT][/COLOR]
[COLOR=#2C2C29][FONT=Tahoma][SIZE=2]&#8230;then reload apache&#8230;[/SIZE][/FONT][/COLOR]
[COLOR=#2C2C29][FONT=Tahoma][SIZE=2]sudo service apache2 reload[/SIZE][/FONT][/COLOR]
[COLOR=#2C2C29][FONT=Tahoma][SIZE=2]&#8230;This got me past the 404 but now i just have an empty page. So on to more tinkering (though I must say zoneminder install/config has been tedious thus far).



I've got the same thing now. Empty page.[/SIZE][/FONT][/COLOR]

---

### Post by rackit on 2013-12-11
Enable errors in you php.ini - see if that gives any clues - too look in your apache logs.

---

### Post by Stjepan225 on 2013-12-12
[B]Deprecated: mysql_pconnect(): The mysql extension is deprecated and will be removed in the future: use mysqli or PDO instead in [B]/usr/share/zoneminder/includes/database.php on line [B]32

**Parse error: syntax error, unexpected end of file in [B]/usr/share/zoneminder/includes/functions.php on line [B]2438**[/B][/B][/B][/B][/B]

---

### Post by SeijiSensei on 2013-12-12
An unexpected end of file in a PHP script often means there is an unmatched bracket.

If you can use a text editor that uses syntax checking, see if adding a "}" at the end of the file and above any closing "?>" PHP tags solves the problem.

(I use the obscure Emacs clone, [jed]("http://www.jedsoft.org/jed/"), myself, but other editors support syntax highlighting as well.)

A check of [mysql_pconnect()](http://www.php.net/manual/en/function.mysql-pconnect.php) shows it will be maintained through PHP 5.5.0. That means you're fine with any version of Ubuntu [before Saucy 13.10]("https://launchpad.net/ubuntu/+source/php5") when PHP 5.5.3 replaced 5.4.9.

---

### Post by Stjepan225 on 2013-12-12
I don't see error in that file, it ends with this:



// For general text in pages outside of tags or quotes so quotes converted to entities
function validHtmlStr( $input )
{
    return( htmlspecialchars( $input, ENT_QUOTES ) );
}


?>

---

### Post by Stjepan225 on 2013-12-12
I was running this command: sudo /etc/init.d/apache2 force-reload

> *miske@miske:~$ sudo /etc/init.d/apache2 force-reload** * Reloading web server apache2                                                 * *
* * The apache2 configtest failed. Not doing anything.*
*Output of config test was:*
*AH00526: Syntax error on line 1 of /etc/apache2/conf-enabled/zoneminder.conf:*
*Alias takes two arguments, a fakename and a realname*
*Action 'configtest' failed.*
*The Apache error log may have more information.*


---

### Post by Butch128 on 2014-07-12
Not sure if anyone is still interested in the solution... but....

Add a } at line 662 of  /usr/share/zoneminder/includes/functions.php

The function buildSelect had the syntax error.

Unfortunately - a host of new problems then come up, such as 

  <script type="text/javascript" src="/javascript/mootools/mootools-core-nc.js"></script>
  <script type="text/javascript" src="/javascript/mootools/mootools-more-nc.js"></script>

Not being defined... To fix create a symbolic link:

ln -s /usr/share/javascript /usr/share/zoneminder/javascript


Hooooly heck... then probing for cameras fails... so you have to...

$command = "arp -a"; in

/usr/share/zoneminder/skins/classic/views/monitorprobe.php

and change to...

$command = "/usr/sbin/arp -a";


I'm starting to not want to use this software.

---

