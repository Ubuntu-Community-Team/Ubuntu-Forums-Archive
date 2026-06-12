---
title: "Mythweb security"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by jba6511 on 2007-06-07
Before I install mythweb, how secure is it to be running behind a router?

---

### Post by dannystaple on 2007-06-08
If this is a ADSL router with NAT/Firewalling, then as long as you have no virtual server routes pointing at mythweb, you will be fine. 

My way of doing this kind of thing is to have only the SSH ports allowed through, and then tunnel in when I want browser access to something on my computer from a remote location.

Alternatively, you could add in some Apache auth stuff to protect the folder if you do want it accessible on the net.

---

### Post by barney_1 on 2007-06-08
I wrote some stuff about adding apache authorization in the community documentation:

[http://help.ubuntu.com/community/MythWeb](http://help.ubuntu.com/community/MythWeb)

---

### Post by dannyboy79 on 2007-06-20
> **barney_1 said:**
> I wrote some stuff about adding apache authorization in the community documentation:

[http://help.ubuntu.com/community/MythWeb](http://help.ubuntu.com/community/MythWeb)

I have found errors on the User Docs page you created and it also doesn't even work for me.

You have this line:

sudo htpasswd /etc/apache2/httpd-passwords MYUSER2

and then you tell us to secure the file with chmod and this is what you put

sudo chmod 640 /etc/httpd/conf/httpd-passwords

As you can see the 2 locations don't match so it errors out. Can you please fix this? Also, when I do this, my mythweb is no longer shown within [http://localhost?](http://localhost?) Do I have to enter [http://localhost/mythweb](http://localhost/mythweb) to get to it, then should it prompt me for a password?

It's my understanding that I can put anything for MYUSER1, is that correct? What if I use my normal user that I use for my system, is this ok? Other guides talk about having to chown the httpd-passwords file but yours doesn't, does this have somethign to do with this not working for me?

What I did when it didn't work, I merely deleted everything again from the /etc/apache2/httpd.conf file and hten I could see the mythweb when I went to localhost, I did however NOT undo the user I added to httpd-passwords so If you explian to me how to get this to work, should I have to do is merely copy and paste what you have noted? Is there anything I have to modify within that file besides the MYUSER1 names? 

Also, maybe you could help with this issue ([http://ubuntuforums.org/showthread.php?t=478980](http://ubuntuforums.org/showthread.php?t=478980)) I am having regarding viewing recordings thru mythweb, it states they aren't there?? Also, I have tons of errors about auotexpire, it stating that the files that are be autoexpired aren't being deleted because they can't be found, just like the error within mythweb. Any suggestions?

---

### Post by barney_1 on 2007-06-20
Thanks for catching that error.  Yes, you do indeed need to enter the mythtv directory in the path on your browser in order to access mythweb after securing it in this method.  This is just a bit more security for mythweb.

This security is important.  Try this search in google:
```
intitle:"MythTV Backend Status"
```

---

### Post by dannyboy79 on 2007-06-20
could you please answer my questions????? If you're a mythtv user and a mythweb user than I would appreciate your help instead of just pointing me to gogle.

---

### Post by FXFman1209 on 2007-06-21
I have also tried your authentication tips, however I'm having a problem...

I've gotten the authentication working fine; it asks me for my username and password and everything. However, after I log in, instead of showing me the MythWeb interface, it gives me an Index view of the thing. Can you help??

---

### Post by dannyboy79 on 2007-06-22
if you mean that it's only showing you  a directory, check this out: [http://ubuntuforums.org/showthread.php?t=440848&highlight=mythweb](http://ubuntuforums.org/showthread.php?t=440848&highlight=mythweb)

now since I have helped you hoepfully, can you please try to help me? did you modify the .htaccess file or did you edit the /var/www/mythtv/httpd-passwords file? can you please also see if you can help on any of my issues above? can you please maybe show me some of your symlinks within /var/www/mythweb/? because I am haviung issues which I have another thread on and maybe you can help. it's here:  [http://ubuntuforums.org/showthread.php?t=478980](http://ubuntuforums.org/showthread.php?t=478980)

thank you if you can provide any feedback at all.

---

### Post by FXFman1209 on 2007-06-23
Alright. Lets see... I don't see a problem adding the user you use to log in to the computer, however I wouldn't necessarily use the same password.

If you have it set up correctly, you will not see mythweb in [http://localhost/](http://localhost/) until AFTER you put in your password. You will have to go to [http://localhost/mythweb/](http://localhost/mythweb/), enter your password, and then it will show up in [http://localhost](http://localhost) until you logout (meaning close the browser).

Also, my httpd-passwords file is chowned to www-data.www-data (meaning the owner is www-data and the group is also www-data), so go ahead and do that. The permissions should be 640.

Also, I didn't like doing it by editing apache (using the whole directory thing). I finally got it to work by editing the .htaccess file instead. Here's the important part of my .htaccess file...

    AuthType           Digest
    AuthName           "MythTV"
    AuthUserFile       /etc/apache2/httpd-passwords
    Require            valid-user
    BrowserMatch       "MSIE"      AuthDigestEnableQueryStringHack=On
#Allow from 192.168.1.
#Satisfy any

Once I did all that it worked perfectly! If there are any problems just let me know.

---

### Post by dannyboy79 on 2007-06-23
and can you comment on the recordings folder, if it's different than default and then what symlinks you have since mine is not working when I try to view recordings thru mythweb, it says file doesn't exist but it does. Thanks soo much for you help thus far!

ok, i tried adding what you said to the /var/www/mythweb/.htaccess and it still isn't working. I even chowned and chmod'd the /etc/apache2/httpd-passwords file. any other suggestions? I can go to localhost and it only shows apache2, then if I enter mythweb on the end of localhost, it says internal error or whatever that error is. Please help

---

### Post by FXFman1209 on 2007-06-23
lrwxrwxrwx 1 root root 26 2007-06-12 11:42 recordings -> /var/lib/mythtv/recordings

Also, when you start Apache and it says :
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
Don't worry about it. I'm pretty sure that its because you don't have a ServerName option in apache2.conf. It won't matter if you have it or not.

I don't really know about the recordings, I've never tried that part of MythWeb. But above is where it records to.

---

### Post by dannyboy79 on 2007-06-24
well it's NOT working and I am at a loss as to why? Im hoping that you can maybe help me figure out why? I keep getting this error:

[http://img264.imageshack.us/img264/5168/internalservererrorzg1.png](http://img264.imageshack.us/img264/5168/internalservererrorzg1.png)

ok, i tried adding what you said to the /var/www/mythweb/.htaccess and it still isn't working. I even chowned and chmod'd the /etc/apache2/httpd-passwords file. i've even tried following the link which is on sheet 1 of this thread and trying to follow those instructions regarding the /etc/apache2/httpd.conf file and still no go????

---

### Post by FXFman1209 on 2007-06-25
Okay, well I never changed anything for the recordings folder.

As for the .htaccess, paste me the relevant lines in yours and I'll try to see whats happening.

---

### Post by dannyboy79 on 2007-06-26
It doesn't matter that my recordings folder is NON-standard does it? Here's the .htaccess relevant section.

AuthType Digest
AuthName "MythTV"
AuthUserFile /etc/apache2/httpd-passwords
Require valid-user
BrowserMatch "MSIE" AuthDigestEnableQueryStringHack=On
#Allow from 192.168.1.
#Satisfy any

the user I added with htdigest was NOT my normal user that I use to log in with, does that matter? this is the owner and permissions for that file:
-rw-r----- 1 www-data www-data 22 2007-06-23 13:04 /etc/apache2/httpd-passwords

i have pasted the rest of the .htaccess file at pastebin, here it is: [http://pastebin.com/936849](http://pastebin.com/936849)

I keep getting the same Internal Apache Error. 
**This is what the error.log shows:**
[Sun Jun 24 07:35:36 2007] [notice] Apache/2.2.3 (Ubuntu) PHP/5.2.1 configured -- resuming normal operations
[Sun Jun 24 17:29:15 2007] [crit] [client 127.0.0.1] configuration error:  couldn't check user.  No user file?: /mythweb
[Sun Jun 24 17:33:29 2007] [crit] [client 127.0.0.1] configuration error:  couldn't check user.  No user file?: /mythweb
[Sun Jun 24 17:58:57 2007] [notice] caught SIGTERM, shutting down
[Sun Jun 24 18:00:54 2007] [notice] Apache/2.2.3 (Ubuntu) PHP/5.2.1 configured -- resuming normal operations
[Mon Jun 25 17:19:20 2007] [notice] Apache/2.2.3 (Ubuntu) PHP/5.2.1 configured -- resuming normal operations

**And this is what the accesss.log shows: **
127.0.0.1 - - [24/Jun/2007:17:29:15 -0500] "GET /mythweb HTTP/1.1" 500 623 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.4) Gecko/20061201 Firefox/2.0.0.4 (Ubuntu-feisty)"
127.0.0.1 - - [24/Jun/2007:17:33:29 -0500] "GET /mythweb HTTP/1.1" 500 623 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.4) Gecko/20061201 Firefox/2.0.0.4 (Ubuntu-feisty)"

UPDATE:
I just found another .htaccess file located within /usr/share/mythtv/mythweb/data/

this is what's in it???? does this matter? Do you have this extra file?
# Allow the webserver to follow symlinks in the data directory, but not to
# execute any commands, browse directory indexes, etc.
    Options -All +FollowSymLinks +IncludesNoExec

ALSO, is your /var/www/mythweb/.htaccess symlink owned by root? which then points to /etc/mythtv/mythweb-htaccess? See below.
/var/www/mythweb# ls -la
drwxr-xr-x  7 root root     4096 2007-06-23 13:14 .
drwxr-xr-x  7 root root     4096 2007-06-19 20:12 ..
drwxr-xr-x  2 root root     4096 2007-06-19 20:13 data
lrwxrwxrwx  1 root root       28 2007-06-19 20:12 .htaccess -> /etc/mythtv/mythweb-htaccess
-rw-r-----  1 root www-data 6262 2007-06-23 13:14 .htaccess~
-rw-r-----  1 root www-data 6257 2007-06-23 13:00 .htaccess~~
-rw-r--r--  1 root root     6294 2007-04-12 04:26 .htaccess.dist
drwxr-xr-x  3 root root     4096 2007-06-19 20:12 includes
drwxr-xr-x  2 root root     4096 2007-06-19 20:12 js
drwxr-xr-x 12 root root     4096 2007-06-19 20:12 modules
-rw-r--r--  1 root root      946 2007-04-12 04:26 mythweb.php
-rwxr-xr-x  1 root root     2531 2007-04-12 04:26 mythweb.pl
drwxr-xr-x  6 root root     4096 2007-06-19 20:12 skins

---

### Post by Wardazo on 2007-06-26
You seem to be using Digest authentification. In the tutorial they use Basic.

This will definitely cause an internal server error if you haven't got that module installed. Try changing AuthType Digest to:

AuthType Basic

---

### Post by dannyboy79 on 2007-06-26
i hope that's it. 

I believe I originally setup a httpd-passwords file using htpasswd command instead of using htdigest command, and I read at that link that I should edit the httpd.conf file and that doesn't even exist???? But I added the file anyway and did everything the link said and it still didn't work.

Then I was told by the guy in this thread to add whatever to the .htaccess file BUT he didn't tell me to remove the htpasswd passwords file and to use htdigest to create a new password file so I think I was kind of mmixing the 2 ways of doing it.

So I found this thread ([http://www.mythtv.org/wiki/index.php/MythWeb](http://www.mythtv.org/wiki/index.php/MythWeb)) which talks about 2 different ways to secure mythweb and when I get home I can see if it worked because I already did the apache2.conf changes and used htpasswd again all thru ssh.

Thanks for the hint. can you look at the link and let me know what you think?

---

### Post by meman63 on 2007-06-26
If you need further help.post the error message.

Regards,
  Meman63

---

### Post by Wardazo on 2007-06-26
> I read at that link that I should edit the httpd.conf

httpd.conf is not used in apache2; however, I've got a feeling I've read somewhere that apache still reads for it to aid migrating from older versions of apache. Please no one quote me on that. Anyway, to simplify the problem get rid of it. 

Make the update in the htacess file (The one on the usr directory is just there for copy and paste  - forget about  it).
> 
So I found this thread ([http://www.mythtv.org/wiki/index.php/MythWeb](http://www.mythtv.org/wiki/index.php/MythWeb)) which talks about 2 different ways to secure mythweb and when I get home I can see if it worked because I already did the apache2.conf changes and used htpasswd again all thru ssh.

I'd just use basic auth for the moment in order to get things up and working. Then try out digest once your application is running. (Digest is far superior).

---

### Post by dannyboy79 on 2007-06-27
> **Wardazo said:**
> httpd.conf is not used in apache2; however, I've got a feeling I've read somewhere that apache still reads for it to aid migrating from older versions of apache. Please no one quote me on that. Anyway, to simplify the problem get rid of it. 

Make the update in the htacess file (The one on the usr directory is just there for copy and paste  - forget about  it).


I'd just use basic auth for the moment in order to get things up and working. Then try out digest once your application is running. (Digest is far superior).

SOLVED!!! Apparently the httpd.conf is called upon within /etc/apache2/apache2.conf BUT it wasn't working, so after I added:

<Directory "/var/www/mythweb">
    Options Indexes FollowSymLinks
    AuthType Basic
    AuthName "MythWeb"
    AuthUserFile /etc/apache2/mythweb-passwords
    require user MYUSER1 MYUSER2
    Order allow,deny
    Allow from 192.168.0.
    Satisfy any
</Directory>
(NOTE: change MYUSER1 & MYUSER2 to whatever users you want)

at the very end of the actual apache2.conf file and followed the rest of the guide for Basic Auth, everything is working. You do have to restart apache2 for this to take effect though versus the .htaccess is suppose to work without restarting apache2.

Now at least it works from within my network, BUT it doesn't work outside my network? I am trying to use a different port I might add. I tried port 8000 and I did change it within /etc/apache2/ports.conf and I also forwarded that same port within my Hardware Router/Firewall but I can't access it from outside the lan. I try this: 
XX.XX.XXX.XX:8000/mythweb
and it doesn't work?

 I am guessing that it something to do with the last 2 lines with apache2.conf and I'll have to play around with it. I guess it's also possible that my work doesn't allow port 8000 OUT possibly. BUT at least it's working within my network. Any suggestions on how to require a password from outside lan and NOT require one when I within my lan? 

I just thought about it, with the current settings above, I am asked for a password when I am within my lan so obivously the suggestions here which is where I got the last 2 lines from([http://www.mythtv.org/wiki/index.php/MythWeb#Apache_Configuration](http://www.mythtv.org/wiki/index.php/MythWeb#Apache_Configuration)) don't work.

---

