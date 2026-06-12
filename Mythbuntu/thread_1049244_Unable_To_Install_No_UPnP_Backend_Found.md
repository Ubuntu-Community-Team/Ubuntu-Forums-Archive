---
title: "Unable To Install: No UPnP Backend Found?"
date: 2009-01-24
forum: Mythbuntu
---

### Post by PeteCress on 2009-01-24
Fresh install of Ubuntu 8.10 from the .ISO with all 225 system updates available at time of install applied.

4096 mb swap partition, rest of the 1tb volume devoted to "/" as Ext3.

Attempting to install MythTV & MythWeb.

Been through this process twice today - more like a dozen times in the past.   Can't make it work

UserID is always "x"  Passwords are always "x", except for the backend PW, which is predetermined each time.

This time I photographed each screen along the way and uploaded the stream to Flickr.

Can somebody flip through the pix and tell me where I'm going wrong?   (if you need more detail, there's a little "All Sizes" icon above the pic).

[http://tinyurl.com/bfjpoq](http://tinyurl.com/bfjpoq)

---

### Post by crez79 on 2009-01-24
I had some problems when I set up too. I think I used [this]("https://help.ubuntu.com/community/MythTV/Install/Troubleshooting") to sort it out.

---

### Post by august495 on 2009-01-24
Try this:

```
sudo dpkg-reconfigure mythtv-database
```

---

### Post by PeteCress on 2009-01-24
> **crez79 said:**
> I had some problems when I set up too. I think I used [this]("https://help.ubuntu.com/community/MythTV/Install/Troubleshooting") to sort it out.

Seems to me that if I do a plain-vanilla install on a fresh copy of Ubuntu that if it doesn't work there's either something wrong with me or the install procedure.

I posted the screen snaps in hopes of finding out which...

I'm about at the end of my string with MythTV.   Seems like hundreds, or even thousands of people are using it, but I just can't get it to work for any length of time.  

The "can't for any length of time..' might reflect on my hardware or even on the reputed mysql MyISAM bug described here: [http://tinyurl.com/brcoc2](http://tinyurl.com/brcoc2).

But right out of the box?  Seems like it's got to be user error (i.e. me...) or a bug in the package.

---

### Post by PeteCress on 2009-01-24
> **august495 said:**
> Try this:

```
sudo dpkg-reconfigure mythtv-database
```

Been there, done that - maybe a half-dozen times.  I think it actually helped once, but that was enough iterations ago that I can't be sure.

But it begs the question of why it would be necessary on a plain-vanilla install onto a newly-built Ubuntu system with all the updates applied.

---

### Post by crez79 on 2009-01-24
> **PeteCress said:**
> Seems to me that if I do a plain-vanilla install on a fresh copy of Ubuntu that if it doesn't work there's either something wrong with me or the install procedure.


I would think so too. I don't know a whole lot about the details because I have only been using linux for a few months. I have found some things are much easier and some are harder. I think things are generally easier to troubleshoot, once you learn the basics. I only know the most basic of the basics, so I seem to fight everything I do. 

You may try to install mythbuntu and then add the ubuntu desktop to that. I used that route on one of my frontends and it worked fine. But that again, is not a fix, just a work around. I installed mythbuntu, not just mythtv. I think they are based on the same thing, but have some differences. I am not sure because I have never used straight up mythtv.

---

### Post by PeteCress on 2009-01-24
> **august495 said:**
> ```
sudo dpkg-reconfigure mythtv-database
```

That didn't abend:
```
x@MythBox:~$ sudo dpkg-reconfigure mythtv-database
[sudo] password for x: 
 * Starting MySQL database server mysqld                                 [ OK ]
```

But it didn't seem to do anything to remedy stuff like this:

```
x@MythBpx:~$ sudo mysqlcheck -u root -p --auto-repair --check --optimize  --all-databases
Enter password: 
mysqlcheck: Got error: 1045: Access denied for user 'root'@'localhost' (using password: YES) when trying to connect

```

Or this (which is what the backend is throwing when I try to do

x@MythBOx:~$ mythtv-setup:
```
console is not interactive, using default 'no']
2009-01-24 16:14:37.036 Unable to connect to database!
2009-01-24 16:14:37.044 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-01-24 16:14:37.129 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-01-24 16:14:37.180 Cannot login to database?
2009-01-24 16:14:37.181 Cannot login to database?

Cannot login to database?
```

---

### Post by august495 on 2009-01-25
Ok, most of my mythtv troubleshooting has been "follow this guide, follow that guide."

> **PeteCress said:**
> 

UserID is always "x"  Passwords are always "x", except for the backend PW, which is predetermined each time.


Did you set a MYSQL root password? If not it's blank and it's not the password generated by mythtv. 

When I enter the SQL command you showed, it asks for my root account  password and then my SQL root password.

---

### Post by PeteCress on 2009-01-25
> **august495 said:**
> When I enter the SQL command you showed, it asks for my root account  password and then my SQL root password.
Same here: it's a two-step process.   First Sudo asks for my Ubuntu root account's PW and then MySQL asks for the MySQL root PW - which is "x' in both cases to keep things simple.

---

### Post by crez79 on 2009-01-25
It seems you are not the [only one that had problems.]("http://ubuntuforums.org/showthread.php?t=675300") Maybe its a bug and not isolated?

---

### Post by enchesss on 2009-01-25
If you have set a password for the root user of mysql and NOT left it blank - you will be unable to access the database from the front end.

I had this problem and followed some tricky instructions to reset the root password - it is more difficult than just updating the database. This enabled the front end to access the database though and i was then able to continue the fun of setting up the backend.

Cant remember where i found the correct how to but some links that had been visisted when i typed "change root password in myth tv" into google were:

[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting) (probably too simple and wont work)

[http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html) (looks much more promising)

---

### Post by elvinatom on 2009-01-26
I had the same problem, so I changed my options to install my frontend with a primary backend.  After the installation I removed the backend and everything went fine.

---

### Post by PeteCress on 2009-01-26
> **crez79 said:**
> It seems you are not the [only one that had problems.]("http://ubuntuforums.org/showthread.php?t=675300") Maybe its a bug and not isolated?

I'm starting to wonder if my case is something to do with [http://tinyurl.com/brcoc2](http://tinyurl.com/brcoc2) ("Corrupt Tables in MySQL after running mythfilldatabase").

I tried to do what they recommend there (dump the DB, "drop" it, and re-create it from the dump) but all the little gotchas along the way - including an access rights issue - made it hopeless.

I've got to think that my problem is basically trivial for somebody who knows their way around MySQL.... but insurmountable for the likes of me.

I've looked at a few alternatives and still believe that, for me,MythTV's functionality is still the gold standard.   The only fly in the ointment being that I can't make it work.

Microsoft Media Center for XP wasn't configurable enough, couldn't handle a digital/analog tuner, and smacked of being a marketing tool as well.

BeyondTV looked promising as it seemed tb a shameless Windows port of Myth.  Certainly the install went smoothly.   But they had a goofy authentication scheme that made it impossible to test the client on different machines.   Also, when I checked their web site there were multiple reports from paid-up users of problems with said scheme - but a total absense of response from BeyondTV support.

The one I'm playing with now is called "SageTV" - also Windows-based.    I've done several installs and they all went without a hitch.   

On the minus side: The client is noticibly more resource-hungry than Myth; I find the UI's button behaviour irritating; and, out of the box, it's keyboard control leaves something tb desired.

On the plus side: It works; it does the jobs that I want to do; and the installs go smooth as butter.  

It also has a nice bit of additional functionality called something like "recording format" where you can choose on a program-by-program basis from a number of recording densities all the way form about 6-7 gigs per hour of program down to 200 megs per hour of program.  That seems to hold promise for remote viewing over WiFi.

That functionality is probably addressable somehow via Myth's "Transcode", but SageTv's is point-and-click and I don't have enough time left over from my day job to cope with "Transcode".

Bottom line, I think I'll pony up the dinero for Sage and go with it - keeping an eye on Myth in hopes that it becomes installable/stable/usable by The Complete Moron...

---

### Post by PeteCress on 2009-01-26
> **crez79 said:**
> It seems you are not the [only one that had problems.]("http://ubuntuforums.org/showthread.php?t=675300") Maybe its a bug and not isolated?

I don't claim any knowledge of Linux or MySQL, but my money is on this one: [http://dwarfurl.com/4a599](http://dwarfurl.com/4a599)  ("Corrupt Tables in MySQL after running mythfilldatabase").

I've tested a few Myth alternatives (MS Media Center, BeyondTV, and SageTV).

To me, Myth is still the gold standard as far as the functionality it promises and resource use go.

Unforunately I still cannot get MythTV to run and my day job is suffering from the effort.

MS Media Center and BeyondTV both fell short for me.

SageTV has it's faults, but it does the job and I've installed it several times now with zero hitches.  The install is quick and effortless - both for the server and the client.

Consequently I think I'm going to pony up the dinero for Sage.  I'll keep looking over my shoulder for a usable MythTV.

---

### Post by PeteCress on 2009-01-27
> **crez79 said:**
> It seems you are not the [only one that had problems.]("http://ubuntuforums.org/showthread.php?t=675300") Maybe its a bug and not isolated?

My money is on: [http://tinyurl.com/brcoc2](http://tinyurl.com/brcoc2)

---

