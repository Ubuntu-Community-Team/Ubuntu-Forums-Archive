---
title: "Help with HTML code (i think)"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by wewantutopia on 2009-12-28
Hello, I have apache, phpmyadmin, php5, mysql etc set up and working on my LAN and over the internet via DynDNS.  I have a wordpress and Jinzora server setup and working.  I just learned (it clicked I guess I already knew) last night that what ever is in the /var/www/ folder is accessable.  I did some experimenting creating a folder and adding links to my music and movie folders.  Sure enough it acts as a file server, SWEET.  Now I wanted to keep this functionality but I don't want the world to have access to my files so I started to figure out password protect it. 

I obviously am a coding noob..  (I know BASIC and can kind of read and do some simple existing code editing)  I realized that if index.html is in the folder I am accessing that is what is displayed.  I created an index.html file in my folder that contains my media links using some password code I found online

```
<form>
<p>ENTER USER NAME : 
  <input type="text" name="text2">
</p>
<p> ENTER PASSWORD :
<input type="password" name="text1">
  <input type="button" value="Check In" name="Submit" onclick=javascript:validate(text2.value,"USERNAME",text1.value,"PASSWORD") >
</p>

</form>
<script language = "javascript">

/*
Script by Anubhav Misra (anubhav_misra@hotmail.com)
Submitted to JavaScript Kit (http://javascriptkit.com)
For this and 400+ free scripts, visit http://javascriptkit.com
*/

function validate(text1,text2,text3,text4)
{
 if (text1==text2 && text3==text4)
 load('SUCESS.htm');
 else 
 {
  load('FAILURE.HTM');
 }
}
function load(url)
{
 location.href=url;
}
</script>

<p align="center"><font face="arial" size="-2">This free script provided by <a href="http://javascriptkit.com">JavaScript Kit</a></font></p>
```

It works fine, requests passwords and directs me to the correct address upon success (the media folder) or failure of password entry.  The only problem is I can still access the media folder if I enter it manually.  How do I fix this.  I'm guessing that the success redirect shouldn't point do a different address but rather allow viewing the contents of the folder.  Is this right?  Any help on how to proceed would be GREATLY appreciated!

Thank you!

---

### Post by headvampyre@hotmail.co.uk on 2009-12-28
hi this is not done in html but in an apache configuration file so goto 

/etc/apache/httpd.conf

then backup the file them open it in text editor
press control+f and type in

Options Includes Indexes FollowSymLinks MultiViews

and remove the word Indexes so it looks like this

Options Includes FollowSymLinks MultiVeiws

also if you need any help with html or css email me @ [email]wiccaguy@googlemail.com[/email]

also do you want a page that is closer to the web standards

---

### Post by wewantutopia on 2009-12-28
Thanks for your response.  I actually don't have /etc/apache, I have /etc/apache2.
Within /etc/apache2 there is an httpd.conf but it is blank.  

Is there anything I could do to this part of the existing code:

```
function validate(text1,text2,text3,text4)
{
 if (text1==text2 && text3==text4)
 load('success.htm');
 else 
 {
  load('failure.htm');
 }
}
function load(url)
{
 location.href=url;
}
</script>
```

That would load the folder that the index is in instead of load a url?

---

### Post by headvampyre@hotmail.co.uk on 2009-12-28
soz i posted wrong file it should be apache2.conf (im used 2 old linux filesystem)

and there isnt much u can do with javascript also try lookin around for sumthin in asp(x) as its more secure but i dont no asp(x) as im only 13 but try to avoid javascript as it can be used to run malicious code against ur server

---

### Post by wewantutopia on 2009-12-28
Again, thanks for the response.  I searched apache2.conf for the terms you listed and none were to be found, nor was the single term index.  Any other ideas?

Better yet, could you (or anyone else) suggest better code / a better way to do this since java script could potentially lead to malicious scripts?  Thanks!

---

### Post by headvampyre@hotmail.co.uk on 2009-12-28
ok so with the config file just add the line 2 it.
and as for another script ill look around the net and also attempt to make a login script
p.s make sure you have mysql-server installed as im writing a php script which uses a database
and phpmyadmin
then create a database called auth and a table called members

to access phpmyadmin goto [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

---

### Post by headvampyre@hotmail.co.uk on 2009-12-28
ok i have rebuilt the page and added a link to php sctips and make sure you have all the files i upload in the same directory and make sure you setup the database in that directory also the database will store the usernames and passwords 

use this for creating login in the database

CREATE TABLE `members` (
`id` int(4) NOT NULL auto_increment,
`username` varchar(65) NOT NULL default '',
`password` varchar(65) NOT NULL default '',
PRIMARY KEY (`id`)
) TYPE=MyISAM AUTO_INCREMENT=2 ;

-- 
-- Dumping data for table `members`
--

INSERT INTO `members` VALUES (1, 'john', '1234');

if you need help mail me and ill respond 2morrow

---

### Post by headvampyre@hotmail.co.uk on 2009-12-28
soz i cant upload the files coz format not supported ill post howtos and the codes 2morrow aswell

---

### Post by wewantutopia on 2009-12-28
Awesome!  thanks for your help!

---

