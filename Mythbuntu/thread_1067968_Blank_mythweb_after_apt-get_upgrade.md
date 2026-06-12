---
title: "Blank mythweb after apt-get upgrade"
date: 2009-02-12
forum: Mythbuntu
---

### Post by Nikas on 2009-02-12
Hello.

I cant use mythweb anymore.
The page is blank..white.. nothing. :-)

This is the packages that got updated. It's in swedish but you can see the names. ;)
```
Följande paket kommer att uppgraderas:
  libapache2-mod-php5 php5 php5-cli php5-common php5-curl php5-dev php5-mysql
  php5-snmp
8 uppgraderade, 0 nyinstallerade, 0 att ta bort och 4 ej uppgraderade.
Behöver hämta 5730kB arkiv.
After this operation, 12,3kB of additional disk space will be used.
Vill du fortsätta [J/n]? J
Läs:1 http://archive.ubuntu.com hardy-security/main php5-cli 5.2.4-2ubuntu5.5 [2                                                                             478kB]
Läs:2 http://archive.ubuntu.com hardy-security/main php5-snmp 5.2.4-2ubuntu5.5 [                                                                             11,7kB]
Läs:3 http://archive.ubuntu.com hardy-security/main php5-mysql 5.2.4-2ubuntu5.5                                                                              [65,2kB]
Läs:4 http://archive.ubuntu.com hardy-security/main php5-curl 5.2.4-2ubuntu5.5 [                                                                             23,7kB]
Läs:5 http://archive.ubuntu.com hardy-security/main libapache2-mod-php5 5.2.4-2u                                                                             buntu5.5 [2471kB]
Läs:6 http://archive.ubuntu.com hardy-security/main php5-common 5.2.4-2ubuntu5.5                                                                              [316kB]
Läs:7 http://archive.ubuntu.com hardy-security/main php5 5.2.4-2ubuntu5.5 [1082B                                                                             ]
Läs:8 http://archive.ubuntu.com hardy-security/main php5-dev 5.2.4-2ubuntu5.5 [3                                                                             64kB]
Hämtade 5730kB på 22s (252kB/s)
(Läser databasen ... 168092 filer och kataloger installerade.)
Förbereder att ersätta php5-cli 5.2.4-2ubuntu5.4 (med .../php5-cli_5.2.4-2ubuntu5.5_i386.deb) ...
Packar upp ersättande php5-cli ...
Förbereder att ersätta php5-snmp 5.2.4-2ubuntu5.4 (med .../php5-snmp_5.2.4-2ubuntu5.5_i386.deb) ...
Packar upp ersättande php5-snmp ...
Förbereder att ersätta php5-mysql 5.2.4-2ubuntu5.4 (med .../php5-mysql_5.2.4-2ubuntu5.5_i386.deb) ...
Packar upp ersättande php5-mysql ...
Förbereder att ersätta php5-curl 5.2.4-2ubuntu5.4 (med .../php5-curl_5.2.4-2ubuntu5.5_i386.deb) ...
Packar upp ersättande php5-curl ...
Förbereder att ersätta libapache2-mod-php5 5.2.4-2ubuntu5.4 (med .../libapache2-mod-php5_5.2.4-2ubuntu5.5_i386.deb) ...
Packar upp ersättande libapache2-mod-php5 ...
Förbereder att ersätta php5-common 5.2.4-2ubuntu5.4 (med .../php5-common_5.2.4-2ubuntu5.5_i386.deb) ...
Packar upp ersättande php5-common ...
Förbereder att ersätta php5 5.2.4-2ubuntu5.4 (med .../php5_5.2.4-2ubuntu5.5_all.deb) ...
Packar upp ersättande php5 ...
Förbereder att ersätta php5-dev 5.2.4-2ubuntu5.4 (med .../php5-dev_5.2.4-2ubuntu5.5_i386.deb) ...
Packar upp ersättande php5-dev ...
Ställer in php5-common (5.2.4-2ubuntu5.5) ...
Ställer in php5-cli (5.2.4-2ubuntu5.5) ...

Ställer in libapache2-mod-php5 (5.2.4-2ubuntu5.5) ...
 * Reloading web server config apache2                                                                                                                [ OK ]

Ställer in php5-snmp (5.2.4-2ubuntu5.5) ...

Ställer in php5-mysql (5.2.4-2ubuntu5.5) ...

Ställer in php5-curl (5.2.4-2ubuntu5.5) ...

Ställer in php5 (5.2.4-2ubuntu5.5) ...
Ställer in php5-dev (5.2.4-2ubuntu5.5) ...

root@mythtv:/#

```

Where do i start looking?

I REALLY need help with this. We use mythweb several times everyday!

---

### Post by Mr. J007K4 on 2009-02-12
I got the same problem. Fixed it by downgrading.

```
sudo aptitude install php5-mysql=5.2.4-2ubuntu5.4
```

I chose the option to downgrade packages: libapache2-mod-php5, php-pear, php5-cli, php5-common and php5-gd. And restarted apache.

```
sudo /etc/init.d/apache2 restart
```

---

### Post by Nikas on 2009-02-12
> **Mr. J007K4 said:**
> I got the same problem. Fixed it by downgrading.

```
sudo aptitude install php5-mysql=5.2.4-2ubuntu5.4
```

I chose the option to downgrade packages: libapache2-mod-php5, php-pear, php5-cli, php5-common and php5-gd. And restarted apache.

```
sudo /etc/init.d/apache2 restart
```

Thanks. Made mythweb work again but i need the php5-snmp and php5-curl-package and when i try to install them the system wants to upgrade again...

Need to see some fast solution to this. :)

---

### Post by buntunub on 2009-02-12
Same problem here. Any suggestions to fix this without downgrade?

---

### Post by ianhaycox on 2009-02-13
It might be worth editing /etc/php5/apache2/php.ini to change error logging and then start mythweb to see what is going wrong.

Hopefully it might be a simple edit to the mythweb php scripts.

---

### Post by buntunub on 2009-02-13
> **ianhaycox said:**
> It might be worth editing /etc/php5/apache2/php.ini to change error logging and then start mythweb to see what is going wrong.

Hopefully it might be a simple edit to the mythweb php scripts.

How do you do that and how would you know what scripts to edit?

---

### Post by khartojo on 2009-02-13
Saw this in my /var/log/apache2/error.log:
<b>Fatal error</b>:  Unknown: Cannot use both zlib.output_compression and output_handler together!! in <b>Unknown</b> on line <b>0</b><br />

Seems to be an old php bug that got reintroduced with latest update.
[http://bugs.php.net/bug.php?id=14241](http://bugs.php.net/bug.php?id=14241)

I don't have a solution right now.

---

### Post by buntunub on 2009-02-13
> **khartojo said:**
> Saw this in my /var/log/apache2/error.log:
<b>Fatal error</b>:  Unknown: Cannot use both zlib.output_compression and output_handler together!! in <b>Unknown</b> on line <b>0</b><br />

Seems to be an old php bug that got reintroduced with latest update.
[http://bugs.php.net/bug.php?id=14241](http://bugs.php.net/bug.php?id=14241)

I don't have a solution right now.

I am getting these same errors in that log file.

---

### Post by mpp on 2009-02-13
I've added some comments to the bug report on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/329053](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/329053)

You can get mythweb working if you edit the apache config (file: /etc/apache2/sites-available/mythweb.conf ) and comment out the following lines:

php_value zlib.output_handler Off
php_value output_handler NULL
php_flag output_handler "NULL"

I'm not sure why that makes a difference, or if it breaks something else.  But it at least gets the main mythweb webpage loading.

have fun()
mike

---

### Post by Nikas on 2009-02-13
> **mpp said:**
> I've added some comments to the bug report on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/329053](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/329053)

You can get mythweb working if you edit the apache config (file: /etc/apache2/sites-available/mythweb.conf ) and comment out the following lines:

php_value zlib.output_handler Off
php_value output_handler NULL
php_flag output_handler "NULL"

I'm not sure why that makes a difference, or if it breaks something else.  But it at least gets the main mythweb webpage loading.

have fun()
mike

Thanks!

Seems to be working!

Just have to wait for the "real" solution now. ;-)

---

### Post by buntunub on 2009-02-14
> **mpp said:**
> I've added some comments to the bug report on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/329053](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/329053)

You can get mythweb working if you edit the apache config (file: /etc/apache2/sites-available/mythweb.conf ) and comment out the following lines:

php_value zlib.output_handler Off
php_value output_handler NULL
php_flag output_handler "NULL"

I'm not sure why that makes a difference, or if it breaks something else.  But it at least gets the main mythweb webpage loading.

have fun()
mike

This worked. Thanks much for your help! :P

---

### Post by zeltak on 2009-02-14
Hi

Still dosent work for me..

i get the following message:

zeltak@ztpc:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2Syntax error on line 104 of /etc/apache2/sites-enabled/mythweb.conf:
Invalid command 'php_value', perhaps misspelled or defined by a module not included in the server configuration

this is my relevant section:
 ############################################################################
    # The following settings relate to PHP config.
    #

        <Files *.php>

        #  These settings are intended for apache 2.x.  If your version of apache
        #  doesn't support php_value, or things like memory_limit aren't working
        #  as expected, then use these settings as examples for your own php.ini
        #  files.
             php_value safe_mode                     0

             php_value memory_limit                  32M

             php_value register_globals              0
             php_value magic_quotes_gpc              0
             php_value file_uploads                  0
             php_value allow_url_fopen               On

            # php_value zlib.output_handler           Off
            # php_value output_handler                NULL

        # Note: php_flag does not work in older versions of php
           # php_flag output_handler                 "NULL"

        </Files>

    ############################################################################



any ideas?

zeltak

---

### Post by buntunub on 2009-02-14
I show line 104 as this -

       ```
php_value safe_mode                     0
```

That could be any number of things, but you could try setting it to 1 and see what happens.

---

### Post by zeltak on 2009-02-14
thx for the answer

unfortunatly setting it to 1 does not help, any other stuff i should try?

thx

Zeltak

---

### Post by dardar on 2009-02-14
> **mpp said:**
> 
You can get mythweb working if you edit the apache config (file: /etc/apache2/sites-available/mythweb.conf ) and comment out the following lines:

php_value zlib.output_handler Off
php_value output_handler NULL
php_flag output_handler "NULL"



I had exactly the same problem with a blank mythweb page after a recent software update.

mpp's fix solved it for me as well. 

Thanks much!

---

### Post by archimedez on 2009-02-14
Did you get it working ?  You might have added some extra character when commenting out the lines required.

> **zeltak said:**
> Hi

Still dosent work for me..

i get the following message:

zeltak@ztpc:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2Syntax error on line 104 of /etc/apache2/sites-enabled/mythweb.conf:
Invalid command 'php_value', perhaps misspelled or defined by a module not included in the server configuration

this is my relevant section:
 ############################################################################
    # The following settings relate to PHP config.
    #

        <Files *.php>

        #  These settings are intended for apache 2.x.  If your version of apache
        #  doesn't support php_value, or things like memory_limit aren't working
        #  as expected, then use these settings as examples for your own php.ini
        #  files.
             php_value safe_mode                     0

             php_value memory_limit                  32M

             php_value register_globals              0
             php_value magic_quotes_gpc              0
             php_value file_uploads                  0
             php_value allow_url_fopen               On

            # php_value zlib.output_handler           Off
            # php_value output_handler                NULL

        # Note: php_flag does not work in older versions of php
           # php_flag output_handler                 "NULL"

        </Files>

    ############################################################################



any ideas?

zeltak

---

### Post by khartojo on 2009-02-14
> **dardar said:**
> I had exactly the same problem with a blank mythweb page after a recent software update.

mpp's fix solved it for me as well. 

Thanks much!

Works for me too. Thx mpp.

---

### Post by zeltak on 2009-02-15
hi

Unfortunately the mpp fix dosent work for me :( any other stuff i can try?

thx

Zeltak

---

### Post by kcox5342 on 2009-02-15
Thank goodness!  I hate when I'm the only one having a problem.  Misery loves company, especially when y'all got fixes!

The commenting out of the three lines didn't work for me and broke Torrentflux as well, but I went back in and just un-commented the last two (after trying the first one on its own), the last two commented out works for both Mythweb and Torrentflux.  Thanks a bunch!  Hopefully some official fix comes out soon enough, but mythweb is essential!!

I'd also like to point out that the MythTV Status page at [http://127.0.0.1:6544/](http://127.0.0.1:6544/) was working even when mythweb wasn't.

Now if someone can explain to me why Mythbuntu Control Centre crashes when it first loads...

---

### Post by mcsmith on 2009-02-15
I had the same symptoms, and the mpp fix worked for me.

Thanks, and good luck to the others.

---

### Post by MrHyde on 2009-02-15
Making the change suggested by mpp did not help me.  However, after making the same changes to /etc/apache2/sites-enabled/mythweb.conf worked.  

Cheers.

---

### Post by pommattski on 2009-02-15
Thanks mpp and MrHyde,
That fixed it for me also. :P
Matt.

---

### Post by alexyz on 2009-02-16
yet another variation.  I had to edit 

  /etc/apache2/conf.d/mythweb.conf

with the same change as mpp specified, all three lines commented out.  I already commented it out in /etc/apache2/sites-available/mythweb.conf - not sure if it's necessary in both places.

---

### Post by lcw on 2009-02-17
Huge help, it worked for me... Thanks very much for the help!

---

### Post by zeltak on 2009-02-18
hi

strange...i dont have a /etc/apache2/conf.d/mythweb.conf...

is that the cause of my problems...what should be in it? can anyone paste an example of their file?

thx

Zeltak

---

### Post by pommattski on 2009-02-18
> **zeltak said:**
> i dont have a /etc/apache2/conf.d/mythweb.conf...If it previously worked, I believe it should be there. Have you tried...```
locate mythweb.conf
```

---

### Post by zeltak on 2009-02-19
hi and thx for the answer

im sure 100% its not there (used locate find etc...). 

Can anyone please post these 2 files so i can copy/paste them (the /etc/apache2/conf.d/mythweb.conf and /etc/apache2/sites-enabled/mythweb.conf) id really appreciate it!

thx

Zeltak

---

### Post by megs on 2009-02-19
Another happy shopper after mpp's fix, editing /etc/apache2/sites-available/mythweb.conf worked for me.

---

### Post by zeltak on 2009-02-21
hi guys

this is a bit ridiculous...everyone else can get it fixes with mpp fix but me :( im asking again if someone can please (with sugar on top!) post their config files here..im missing the /etc/apache2/conf.d/mythweb.conf .

thx...im really lost without mythweb (thats how i do 95% of my recordings..)


Zeltak

---

### Post by ianhaycox on 2009-02-21
I don't have a /etc/apache2/conf.d/mythweb.conf file just the one in sites-available and it works OK.

Did you manage to remove the error you mentioned earlier "Invalid command 'php_value'" ?

---

### Post by zeltak on 2009-02-22
no i cant get rid of it

here is the output:

zeltak@ztpc:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2
Syntax error on line 104 of /etc/apache2/sites-enabled/mythweb.conf.save:
Invalid command 'php_value', perhaps misspelled or defined by a module not included in the server configuration
   ...fail!


even if i mark all the section off (#) i still get the same message..i sure could use some help here

thx again

Zeltak

---

### Post by ianhaycox on 2009-02-22
Note that the error is in the file /etc/apache2/sites-enabled/mythweb.conf.**[COLOR="Red"]save[/COLOR]**  

so it looks like there is a bit of confusion with filenames/links and apache is reading your old 'backup' copy and not the new editted version with stuff commented out.

You should have something like this:

```

ian@ianh:~$ ls -l /etc/apache2/sites-enabled/
total 0
lrwxrwxrwx 1 root root 26 2009-01-23 13:41 000-default -> ../sites-available/default
lrwxrwxrwx 1 root root 27 2009-02-15 14:03 bnb.conf -> ../sites-available/bnb.conf
lrwxrwxrwx 1 root root 31 2009-01-23 14:52 mythweb.conf -> ../sites-available/mythweb.conf
ian@ianh:~$ ls -l /etc/apache2/sites-available/
total 36
-rw-r--r-- 1 root root  443 2009-02-15 14:01 bnb.conf
-rw-r--r-- 1 root root  950 2008-09-19 15:41 default
-rw-r--r-- 1 root root 7366 2008-09-19 15:41 default-ssl
-rw-r--r-- 1 root root 8920 2009-01-23 14:52 mythweb.conf
ian@ianh:~$ 


```

note the links from available to enabled.

I'd suggest cleaning up the links etc. and move any backups into your /home to avoid problems.

---

### Post by zeltak on 2009-02-22
thx for the reply ianhaycox

this is some progress :) i managed to clean up the stuff as you said. i noticed that apache looks for the conf file at the sites-enabled folder. so i just copied the mythweb.conf file from the sites-avilable to the sites-enabled folder but i still get this error:

zeltak@ztpc:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2
 * We failed to correctly shutdown apache, so we're now killing all running apache processes. This is almost certainly suboptimal, so please make sure your system is working as you'd expect now!
 ... waiting Syntax error on line 104 of /etc/apache2/sites-enabled/mythweb.conf:
Invalid command 'php_value', perhaps misspelled or defined by a module not included in the server configuration
   ...fail!


How should i proceed?

thx

Zeltak

---

### Post by ianhaycox on 2009-02-22
Really the entries in site-available should be links, but it's not that important at the moment. 

Attached is my original mythweb.conf. If the only edits you have made are to fix the php problem I suggest you copy the attachment to sites-available as mythweb.conf, delete the version in sites-enabled then run,

```

$ sudo a2ensite mythweb.conf

```

to correct the links. Obviously backup your copies first just in case.

Restart apache and visit [http://localhost/mythweb/](http://localhost/mythweb/) to see if it either works or displays a blank page. Hopefully this should straighten everything out before we start editing anything.

For completeness what's the output of:

```

$ dpkg -l | grep php
ii  libapache2-mod-php5                        5.2.6-2ubuntu4.1                        server-side, HTML-embedded scripting languag
ii  php5                                       5.2.6-2ubuntu4.1                        server-side, HTML-embedded scripting languag
ii  php5-common                                5.2.6-2ubuntu4.1                        Common files for packages built from the php
ii  php5-gd                                    5.2.6-2ubuntu4.1                        GD module for php5
ii  php5-mcrypt                                5.2.6-0ubuntu2                          MCrypt module for php5
ii  php5-mysql                                 5.2.6-2ubuntu4.1                        MySQL module for php5
ii  phpmyadmin                                 4:2.11.8.1-1                            MySQL web administration tool

```

---

### Post by zeltak on 2009-02-22
thx ianhaycox

I really really appreciate your help.

using your file and following your instructions unfortunately dont work i still get:

sudo /etc/init.d/apache2 restart
 * Restarting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sun Feb 22 14:26:10 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sun Feb 22 14:26:10 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
   ...done.


the output of dpkg -l | grep php

zeltak@ztpc:~$ dpkg -l | grep php
ii  libapache2-mod-php5                        5.2.6-2ubuntu4.1                        server-side, HTML-embedded scripting languag
ii  php-config                                 1.10.11-1                               Your configuration's swiss-army knife
ii  php-pear                                   5.2.6-2ubuntu4.1                        PEAR - PHP Extension and Application Reposit
ii  php5                                       5.2.6-2ubuntu4.1                        server-side, HTML-embedded scripting languag
ii  php5-cli                                   5.2.6-2ubuntu4.1                        command-line interpreter for the php5 script
ii  php5-common                                5.2.6-2ubuntu4.1                        Common files for packages built from the php
ii  php5-mysql                                 5.2.6-2ubuntu4.1                        MySQL module for php5


What do you think i should do next?

thx alot again

Zeltak

---

### Post by ianhaycox on 2009-02-22
What happened when you went to your MythWeb page ? Did you get a 404 error, or a blank page, or something else ?

I don't really understand the VirtualHost warning because there are no VirtualHost definitions in the Mythweb.conf file (unless they are implied by omission).

---

### Post by zeltak on 2009-02-22
hi again

so after i transfer you config file and issue sudo a2ensite mythweb.conf
i get a message saying 
enabling site mythweb.conf.
Run '/etc/init.d/apache2 reload' to activate new configuration!

which i do and then i get the warning again:

zeltak@ztpc:~$ /etc/init.d/apache2 reload
Syntax error on line 104 of /etc/apache2/sites-enabled/mythweb.conf:
Invalid command 'php_value', perhaps misspelled or defined by a module not included in the server configuration
   ...fail!

when i go to the mythweb site i get a 404 not found 

hope it helps

Zeltak

---

### Post by ianhaycox on 2009-02-23
I'm at a bit of a loss. The comments in mythweb.conf suggest the php_* setting are only for apache2, which you have. So they should work.
I guess there is some other configuration somewhere that conflicts.

The last suggestion I can come up with is to carefully comment out (or delete) the lines in that section of mythweb.conf, restart apache and good luck.

Re-installing apache/php/mythweb might be an option, but seems a bit drastic.

Maybe someone else can shed a little more light ?

---

### Post by pommattski on 2009-02-23
> **zeltak said:**
> when i go to the mythweb site i get a 404 not found 
Note that the original problem that this thread discussed and fixed was that a blank page was served when accessing mythweb following an update.
Ie. Apache was responding to requests for the page, but a php problem meant that no html was written to the page.

Also, what *exactly* is at line 104 of your mythweb.conf file?

---

### Post by zeltak on 2009-02-24
Hi pommattski

The line 104 says:

    php_value safe_mode                     0


but when i edit this out the error message moves to line 105 and so on...
i must add that i tried un-installing mythweb and installing again and it did nor work. also if i comment out the whole section:

 ############################################################################
    # The following settings relate to PHP config.
    #

        <Files *.php>

        #  These settings are intended for apache 2.x.  If your version of apache
        #  doesn't support php_value, or things like memory_limit aren't working
        #  as expected, then use these settings as examples for your own php.ini
        #  files.
            php_value safe_mode                     0

            php_value memory_limit                  32M

            php_value register_globals              0
            php_value magic_quotes_gpc              0
            php_value file_uploads                  0
            php_value allow_url_fopen               On

            php_value zlib.output_handler           Off
            php_value output_handler                NULL

        # Note: php_flag does not work in older versions of php
            php_flag output_handler                 "NULL"

        </Files>


then the apache server starts but with no mythweb obviously

thx

Zeltak

---

### Post by willo8allthepies on 2009-03-02
Hi Zeltak,

Did you ever get to a fix with this?  I am still getting the same line 104 error as you were getting.  Is it something to do with still being on Hardy I wonder?

Thanks

---

### Post by zeltak on 2009-03-03
hi

what i ended up doing through frustration was having a friend of mine (linux guru) come over and fix it. he re-installed php, added some config options etc...i really cant tell you what he did but it took him like an hour. let me know if you still need help..ill call him up and try to reproduce the solution

Best 

Zeltak

---

### Post by nunrgguy on 2009-03-16
Has there been any further movement on this does anyone know. I had the same problem. The fix worked for me with only the first line commented, not the other two. Since then another system update has occurred and it's back to square one with mythweb broken with a white screen - config file is unchanged.

---

### Post by nunrgguy on 2009-03-22
bump?

---

### Post by nunrgguy on 2009-03-25
So is mythweb permanently busted at the moment?

---

### Post by cknight725 on 2009-04-01
WOOT!

mpp's fix worked for me -- edited /etc/apache2/sites-available/mythweb.conf .  Incidentally, I'm running Mythbuntu 7.10.

Thanks!

---

### Post by nunrgguy on 2009-04-09
Still busted here

---

### Post by mpp on 2009-04-11
Well there seems to have been an update to apache or mythweb recently which has again killed mythweb.  Or maybe I'm doing something wierd?

When I go to mythweb in my browser all I see is 4 links, a search box, and the mythtv logo which doesn't load.  All the CSS and all the other links and images are missing.

Is anyone else having this problem?

Incidentally, I re-enabled those commented out sections in my mythweb apache configuration in case that was the cause, but this did not fix it.

What's changed?  Have other people seen this problem too?

I'm running Ubuntu Intrepid AMD64.

have fun()
mike

---

### Post by mpp on 2009-04-11
Oh ... scratch that!!  I have found it was a dead session in the mysql table "mythweb_sessions" from when I accessed mythweb from my mobile phone!  Solution was simply to drop all rows in that table, that is to run the following command in mysql: delete from mythweb_sessions;

Incidentally, now that I've re-enabled those other parameters in my apache config file mythweb is working fine.  It seems whatever changed in the recent mythtv or apache upgrades from the Ubuntu repositories fixed the problem from several weeks ago.

have fun()
mike

---

### Post by Mister.Vash on 2009-04-16
nunrgguy, did you check and see if you had the old mythweb-htaccess file?

From the launchpad bug report, renaming/removing the /etc/mythtv/mythweb-htaccess seems to take care of the issue.  It worked for me
Here is the post from launchpad [https://bugs.launchpad.net/ubuntu/+source/php5/+bug/329053/comments/14](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/329053/comments/14)

---

### Post by jbman on 2009-04-16
I updated my 8.04 box and had no problems. I did not have the password access turned on so maybe that is where is fail is happening.

---

### Post by BillDozer on 2009-05-04
> **mpp said:**
> I've added some comments to the bug report on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/329053](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/329053)

You can get mythweb working if you edit the apache config (file: /etc/apache2/sites-available/mythweb.conf ) and comment out the following lines:

php_value zlib.output_handler Off
php_value output_handler NULL
php_flag output_handler "NULL"

I'm not sure why that makes a difference, or if it breaks something else.  But it at least gets the main mythweb webpage loading.

have fun()
mike

Thanks man, this did the job for me. :-)

---

### Post by krizze on 2009-07-06
A little old thread, but I solved this by doing a:
sudo a2enmod php5
sudo /etc/init.d/apache2 restart

Don't know why it was suddenly disabled - I was fooling around with some ssl-stuff.

---

### Post by bhamail on 2011-08-16
FWIW, I saw the same blank pages behavior (though some pages still worked).
Commenting out the suggested lines had no effect.
Increasing the php memory limit DID fix this for me:

sudo vi /etc/apache2/sites-available/mythweb.conf

then found existing line:
php_value memory_limit                  64M

and changed it to:
php_value memory_limit                  512M

save, reboot, and "Recorded Programs", "Searches", etc pages load fine again.

The versions of things I am running:
mythtv         0.23.1+fixes26
mythweb        0.23.1+fixes26

Ubuntu 10.04.3 LTS

Dan

---

### Post by nickrout on 2011-08-16
> **bhamail said:**
> 
The versions of things I am running:
mythtv         0.23.1+fixes26
mythweb        0.23.1+fixes26

Ubuntu 10.04.3 LTS

Dan

You are running an old and unsupported version of mythtv. 0.24-fixes is what you really want, if you want support.

---

