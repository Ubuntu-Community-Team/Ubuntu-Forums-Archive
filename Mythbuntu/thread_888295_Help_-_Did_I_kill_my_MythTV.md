---
title: "Help - Did I kill my MythTV???"
date: 2008-08-13
forum: Mythbuntu
---

### Post by GLMontyWV on 2008-08-13
Not sure what happened.  Was running fine.  Installed the KDE desktop to try it out, decided it wasn't what I wanted and unclicked it in the control center.  Now I can't get the front end to start at all.

From terminal

```
monty@monty-mythpc:~$ mythfrontend
2008-08-13 00:31:40.854 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-13 00:31:40.855 Configuration::Load - Error parsing: /home/monty/.mythtv/config.xml at line: 1  column: 1
2008-08-13 00:31:40.855 Configuration::Load - Error Msg: unexpected end of file
2008-08-13 00:31:41.650 XScreenSaver support enabled
2008-08-13 00:31:41.651 DPMS is active.
2008-08-13 00:31:41.651 Empty LocalHostName.
2008-08-13 00:31:41.651 Using localhost value of monty-mythpc
2008-08-13 00:31:41.651 Configuration::Load - Error parsing: /home/monty/.mythtv/config.xml at line: 1  column: 1
2008-08-13 00:31:41.651 Configuration::Load - Error Msg: unexpected end of file
2008-08-13 00:31:41.659 New DB connection, total: 1
2008-08-13 00:31:41.662 Connected to database 'mythconverg' at host: localhost
2008-08-13 00:31:41.663 Closing DB connection named 'DBManager0'
2008-08-13 00:31:41.663 Primary screen 0.
2008-08-13 00:31:41.664 Connected to database 'mythconverg' at host: localhost
2008-08-13 00:31:41.665 Using screen 0, 1280x960 at 0,0
2008-08-13 00:31:41.671 New DB connection, total: 2
2008-08-13 00:31:41.672 Connected to database 'mythconverg' at host: localhost
2008-08-13 00:31:41.673 Unexpected DB Schema version.  Waiting to see if DB is being upgraded.
2008-08-13 00:31:46.684 Timed out waiting.
2008-08-13 00:31:46.685 This version of MythTV requires an updated database schema. Please run mythtv-setup or mythbackend to update your database.
monty@monty-mythpc:~$ 
```

I've run the mythtv-setup to update the database but it doesn't help.  Have I lost it?

Thanks!

Monty

---

### Post by funkydan2 on 2008-08-13
What's in the file /home/monty/config.xml?

It should be something like
```

<Configuration>
  <UPnP>
    <UDN>
      <MediaRenderer>082d126c-e436-482f-87b1-51315345679a</MediaRenderer>
    </UDN>
    <MythFrontend>
      <DefaultBackend>
        <DBHostName>XXX.XXX.XXX.XXX</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>this-is-a-password</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>0</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>

```

---

### Post by GLMontyWV on 2008-08-13
[QUOTE=funkydan2;5579250]What's in the file /home/monty/config.xml?

It appears to be completely empty.  :(

Monty

---

### Post by GLMontyWV on 2008-08-13
OK, I've reinstalled all the components and recreated the config.xml file.

Front end now starts but none of my recordings are there.  

:confused:

Monty

---

### Post by DemonBob on 2008-08-13
Is thier any files under /var/lib/mythtv/recordings? 

If thier is then you probably need to run mythrebuilddatabase. [http://mythtv.org/wiki/index.php/Myth.rebuilddatabase.pl](http://mythtv.org/wiki/index.php/Myth.rebuilddatabase.pl)

---

### Post by GLMontyWV on 2008-08-13
> **DemonBob said:**
> Is thier any files under /var/lib/mythtv/recordings? 

If thier is then you probably need to run mythrebuilddatabase. [http://mythtv.org/wiki/index.php/Myth.rebuilddatabase.pl](http://mythtv.org/wiki/index.php/Myth.rebuilddatabase.pl)

There are files there but I can't find that script to run it, where do I find it?

Thanks!

Monty

---

### Post by DemonBob on 2008-08-13
/usr/share/doc/mythtv-backend/contrib

you'll have to extract it since it is compressed.

---

### Post by GLMontyWV on 2008-08-13
> **DemonBob said:**
> /usr/share/doc/mythtv-backend/contrib

you'll have to extract it since it is compressed.

Got it, extracted it to my Desktop, can't run it.

I've tried 

```
monty@monty-mythpc:~/Desktop$ dir
Bills\ Pics		       myth.rebuilddatabase.pl
danny.jpg		       MythTVOS-2008
dban-1.0.7_i386.iso	       MythTVOS-2008.torrent
Drivers			       Pigeon\ forge\ itinerary.odt
FelBlog092a_smf.zip	       puppy-4.00-k2.6.21.7-seamonkey.iso
felblog_940_smf		       smf_1-1-4_upgrade
felblog_940_smf.zip	       smf_1-1-5_install.zip
game.dcr		       SMF_Quick_Theme_Changer_1.0.0.zip
htaccessnew.txt		       speeding(2).dir
htaccess.zip		       speeding.dir
jfusion\ 1.0.5a\ component     TPv1.05beta1(2).zip
jre-6u6-linux-i586-rpm(2).bin  TPv1.05beta1.zip
jre-6u6-linux-i586-rpm.bin     ubuntu-8.04-desktop-i386.iso
jre-6u6-linux-x64-rpm.bin      VersionTracker_Pro_Windows_4_1_cn0074.exe
kubuntu-8.04-desktop-i386.iso  weeklyinsert_small.pdf
logo.png
monty@monty-mythpc:~/Desktop$ myth.rebuilddatabase.pl --try_default
bash: myth.rebuilddatabase.pl: command not found
monty@monty-mythpc:~/Desktop$ 

```

So how do I run it?

Thanks!

Monty

---

### Post by DemonBob on 2008-08-13
It's a perl script. 

I believe add a pl before it 
```

sudo pl myth.rebuilddatabase.pl

```

---

### Post by GLMontyWV on 2008-08-14
OK, got this far

```
monty@monty-mythpc:~$ sudo /usr/local/bin/myth.rebuilddatabase.pl --dbhost localhost --user mythtv --pass password
DBI connect('database=mythconverg:host=localhost','mythtv',...) failed: Access denied for user 'mythtv'@'localhost' (using password: YES) at /usr/local/bin/myth.rebuilddatabase.pl line 191
Cannot connect to database ()

```

Appreciate the help, feel like I am close.

THANKS!

Monty

---

### Post by DemonBob on 2008-08-14
You can get your mysql mythtv user and password from /etc/mythtv/mysql.txt. Besure not to edit this file though. 

Try using the user name and password in this file to run the script.

---

### Post by GLMontyWV on 2008-08-14
That's what I used in post 10, it didn't seem to like all that.  :???:

Really thought it was going to work.  I'll try again earlier tonight when I'm a little fresher.  Appreciate the direction!!!

Thanks!

Monty

---

### Post by perkhouse on 2009-03-29
resolution???

---

