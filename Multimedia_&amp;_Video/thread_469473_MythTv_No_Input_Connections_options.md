---
title: "MythTv No Input Connections options"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by Copland Audio on 2007-06-09
Hello - 
Are there any common reasons there are no input connections options coming up when I'm setting up MythTv?  I've followed the directions to the letter on the community docs for Feisty, and this is where I've stalled - I just get no data under the Input Connections when I select it.  Any suggestions would be appreciated!

---

### Post by Copland Audio on 2007-06-09
I should say that I'm using a Hauppage pvr-150 attempting to use my video signal direct to my computer monitor (no TV).  There's no cable box decoder or anything like that, my signal comes right from the cable from the wall...

---

### Post by newlinux on 2007-06-10
very odd. in mythtv-setup does it even list your tuner after you have defined it? Have you tried running mythtv-setup from the terminal to see if it outputs any errors? You might try deleting and readding the card and then seeing if you can assign a video source to the input connection.

---

### Post by Copland Audio on 2007-06-10
I'm able to play TV using Mplayer, so that tests out that at least the TV signal is getting to the card.  I've seen a couple other threads with this problem, and will try reinstalling the database - The error message when mythfilldatabase only stays on the screen for a second, so I don't know how to troubleshoot from there.  (I'm a bit of a noob).  It seems like the video0 from the capture card isn't making it to the input portion of the setup for some reason.  I'll try a few things and post back.  In the meantime, chime in with any suggestions.

---

### Post by dara on 2007-06-10
I'm having the same problem with my setup.  I had the whole thing working in Edgy and I've gotten the card (PCHDTV HD-3000) to work under the latest MythDora (but not wireless - one of the reasons I prefer Ubuntu is I have canned solutions for getting my wireless and SPDIF sound to work under Ubuntu - both of the these give me trouble under Fedora).  

I followed some instructions in another post ([http://ubuntuforums.org/showthread.php?t=419253](http://ubuntuforums.org/showthread.php?t=419253)) to try get my card to work and now MythTV can see my card under the DVB driver (which is the only driver that has ever worked for me), but as soon as I hit the Finish Key in the setup GUI, it isn't there in the list!  Hopefully this thread will tell me what I'm doing wrong - it's very frustrating when things used to work, but now don't.

Dara

---

### Post by newlinux on 2007-06-10
> **dara said:**
> I'm having the same problem with my setup.  I had the whole thing working in Edgy and I've gotten the card (PCHDTV HD-3000) to work under the latest MythDora (but not wireless - one of the reasons I prefer Ubuntu is I have canned solutions for getting my wireless and SPDIF sound to work under Ubuntu - both of the these give me trouble under Fedora).  

I followed some instructions in another post ([http://ubuntuforums.org/showthread.php?t=419253](http://ubuntuforums.org/showthread.php?t=419253)) to try get my card to work and now MythTV can see my card under the DVB driver (which is the only driver that has ever worked for me), but as soon as I hit the Finish Key in the setup GUI, it isn't there in the list!  Hopefully this thread will tell me what I'm doing wrong - it's very frustrating when things used to work, but now don't.

Dara



What do your backend logs state after you run mythtv-setup? (cat /var/log/mythtv/mythbackend.log) How about  the terminal output from mythtv-setup when you run it? I've only seen this particular problem with database corruption, which I would recommend you reinstall the database. If you post these outputs I can help diagnose more.

Commands to reinstall database:

```

sudo apt-get remove --purge mythtv-database mysql-server-5.0
sudo apt-get install mysql-server-5.0 mythtv-database
```

I'd wait to do this until we verify there is a problem with your database.

---

### Post by dara on 2007-06-11
newlinux,

Thanks for the suggestions.  I didn't know about that log file.  It does seem to offer some hints for what I'm doing wrong.  I read the instructions ([https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O)) more carefully this time and I did comment out the line in the my.cnf file.  Here is my output after trying to add the card but failing (at 8:40 PM and once before too).  It's a bit cryptic to me, but I'll keep looking at it.  I'd be happy to hear any more suggestions. (Perhaps this will help the original poster too).

- Dara

```

2007-06-10 20:23:15.709 Using runtime prefix = /usr
2007-06-10 20:23:16.026 New DB connection, total: 1
2007-06-10 20:23:16.102 Connected to database 'mythconverg' at host: localhost
2007-06-10 20:23:16.140 Current Schema Version: 
2007-06-10 20:23:16.166 Newest Schema Version : 1160
2007-06-10 20:23:16.183 New DB connection, total: 2
2007-06-10 20:23:16.271 Connected to database 'mythconverg' at host: localhost
2007-06-10 20:23:16.467 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2007-06-10 20:23:16.481 New DB connection, total: 3
2007-06-10 20:23:16.484 Connected to database 'mythconverg' at host: localhost
2007-06-10 20:23:16.487 Inserting MythTV initial database information.
2007-06-10 20:23:16.489 New DB connection, total: 4
2007-06-10 20:23:16.491 Connected to database 'mythconverg' at host: localhost
2007-06-10 20:23:16.493 Upgrading to schema version 1112
2007-06-10 20:23:16.563 DB Error (Performing database upgrade): 
Query was: CREATE TABLE IF NOT EXISTS dtv_privatetypes (  sitype varchar(4) NOT NULL default '',  networkid int(11) NOT NULL default '0',  private_type varchar(20) NOT NULL default '',  private_value varchar(100) NOT NULL default ''); 
Error was: Driver error was [2/2013]:
QMYSQL3: Unable to execute query
Database error was:
Lost connection to MySQL server during query
 
new version: 1112
2007-06-10 20:23:16.580 Database Schema upgrade FAILED, unlocking.
2007-06-10 20:23:16.582 Couldn't upgrade database to new schema
2007-06-10 20:40:40.744 Using runtime prefix = /usr
2007-06-10 20:40:40.837 New DB connection, total: 1
2007-06-10 20:40:40.879 Connected to database 'mythconverg' at host: localhost
2007-06-10 20:40:40.884 Current Schema Version: 
2007-06-10 20:40:40.886 Newest Schema Version : 1160
2007-06-10 20:40:40.888 New DB connection, total: 2
2007-06-10 20:40:40.890 Connected to database 'mythconverg' at host: localhost
2007-06-10 20:40:40.892 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2007-06-10 20:40:40.894 New DB connection, total: 3
2007-06-10 20:40:40.895 Connected to database 'mythconverg' at host: localhost
2007-06-10 20:40:40.899 Told to create a NEW database schema, but the database
already has 8 tables.
If you are sure this is a good mythtv database, verify
that the settings table has the DBSchemaVer variable.

2007-06-10 20:40:40.900 Database Schema upgrade FAILED, unlocking.
2007-06-10 20:40:40.901 Couldn't upgrade database to new schema


```

---

### Post by newlinux on 2007-06-11
That looks like database corruption (which I've seen quite often unfortunately). I recommend reinstalling with the commands I sent above.

---

### Post by dara on 2007-06-11
Thanks, that worked (I would have never figured that out).  I do see that my DVB drivers are gone after rebooting though - can I ask how to make the result of the following code permanent?  After that I'm set (besides having an anemic machine that doesn't play HD smoothly yet - I'm thinking of getting a Dell E520N, but that's another thread).

```


sudo modprobe -rv cx88-dvb
sudo modprobe -rv cx8800
sudo modprobe -rv cx88-blackbird
sudo modprobe -v cx88-dvb
sudo modprobe -v cx8800
ls -l /dev/dvb/adapter0
ls -l /dev|grep video
dmesg


```

---

### Post by newlinux on 2007-06-11
It looks like with those commands you are removing and reinserting the cx88-dvb and cx8800 modules and completely removing (blacklisting) cx88-blackbird.

You probably just need to load the cx88-dvb and cx8800 modules at boot. To do this you add the modules to the /etc/modules file which gets loaded at boot:

```

gksudo gedit /etc/modules

```

and add 

```

blacklist cx88-blackbird
cx88-dvb
cx8800 

```


to the end of the file. Save and exit. at next reboot those modules should automatically be loaded.

Give it a try. glad the previous suggestion worked for you.

---

### Post by newlinux on 2007-06-11
Also, I'm curious - what are your machine specs?

---

### Post by Copland Audio on 2007-06-11
I too am up and running, albeit partially.  I reinstalled the database using your commands, was able to assign Input Connections, and have a signal to watch TV.  I have only 2 problems left.  1. I'm only getting (it seems) local channels - not my basic cable channels (Comedy Central, Discovery, etc) I'm getting static with those.  Is this something with...I don't even know..?

Also, I don't have my remote control for my PVR-150 working.  Is this a configuration in Myth I need to address?

Aside from those 2 things, I get a decent picture, am able to scroll back, (I haven't recorded anything yet, but I'm assuming that works)...so... I'm sort-of up and running.

I have a P4 HP Pavilion with only 512 mb of RAM and only an 80GB HD, but I believe I've allocated correctly, and I'd like to see what I can do with this old machine for a while...

Thanks in advance for any help!

---

### Post by tgm4883 on 2007-06-11
You must install LIRC for your remote control

Here is a link to a guide for Lirc on Feisty.  There is a link on that page for Lirc on Edgy if you need it
[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

---

### Post by Copland Audio on 2007-06-11
Thanks for your help with lirc - I found that after very little digging right after I posted, but I appreciate the help, and thank-you!

Now it's on to the question of why I'd only get local stations and not cable stations.  It seems like all my channels above 15 are snow.  Maybe there's something with the video source I should verify?  

FYI, when I reinstalled the database, I didn't reconfigure any passwords for the mythconverg mysql database.  Could this be a problem?  

This problem of getting some channels but not all is a bit strange, and I can't find any threads on it, so... maybe just being guided to the right area may help.  

Thanks again!

---

### Post by newlinux on 2007-06-11
What happens when you scan for channels in mythtv-setup? What are your scan settings?

---

