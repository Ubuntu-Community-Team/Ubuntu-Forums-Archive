---
title: "Fiesty Upgrade and MythTV"
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by djseto on 2007-04-19
I finally got MythTV working on 6.10 edgy. Before I make the jump to 7.x, can someone tell me what the pitfalls may be? I want the latest and greatest, but I also dont want to spend hours getting MythTV to work again. Is there a "rollback" or "uninstall" option in case Fiesty breaks everything and I just want to go back to the way things were? I am new to linux in general so I'm a little hesitant about this upgrade considering things are finally working with stability in 6.10

thanks

---

### Post by Gina on 2007-04-19
If you've got things working well with what you've got why upgrade? 6.10 is fully supported and known to be stable.  I know the full version of Feisty Fawn (7.04) has now been released but unless you have a good reason to upgrade I'd stick with what works.

If you do want to upgrade you could backup your present installation to another drive or partition (if you have one) using partimage or suchlike.

---

### Post by reclusivemonkey on 2007-04-19
I agree with Gina. "If it ain't broke, don't fix it". I have a 6.10 MythTV be/fe in the lounge, and a Fesity desktop. My Feisty desktop has a Myth FE on, and it connects fine. If you only have one machine I know that's not much of a consideration, but it just shows there is nothing really new in Feisty MythTV. If you have MythTV working, I would leave it alone.

---

### Post by superm1 on 2007-04-19
The major changes for the feisty packages of mythtv are packaging, mysql changes, permissions changes.

Well i'll throw out a few points for the feisty upgrade (changes to its packaging and related packages), if none of these appeal to you, don't bother for now.

1) You've got a HD HomeRun hidef network capture device and want to capture QAM
2) You've got some stability issues with your machine with recordings or live tv. (
3) You have issues with ivtv drivers and want to try a newer version. (New IVTV version)
4) You are sick of rebuilding ivtv drivers every time you upgrade the kernel (IVTV Included)
5) You don't regularly back up your mysql database, but want to start.  (Feisty adds a cron job for you to do it)
6) You don't like the AV sync problem in xine for your DVDs.  (Feisty xine fixes this package)
7) You are running amd64, and can't play wmv3 files in misc players.  (Feisty mplayer and a few others have wmv3 support without a w32codecs type package)
8) Your hidef content doesn't play smoothly on your TV using an nvidia card.  (Feisty nvidia drivers support a few new options that will improve hidef performance)

So again, if you think any or several of those ideas meet you, then I say upgrade.  Elsewise, if it ain't broke, don't fix it :)

---

### Post by djseto on 2007-04-19
I am running 32bit version of 6.10 on an AMD Athalon 64 x2 and I do have HD being recorded/playback, but everything plays back fine, so I guess  I'll leave it alone for now.I do have a weird problem with my DVD drive reading CD's, but as soon as I pop in a DVD, it fixes itself, but I can live with that over a complete upgrade and possible nightmare of starting over.

---

### Post by rbm0307 on 2007-04-19
If your 6.10 install is running fine and customized with the feature set you desire, then let it be.

I have been struggling for several days now with a fe/be installation of MythTV on Feisty.  Random code crashes, freezing, unexpected Myth fe reboots are some of the problems I'm currently encountering.  I'd recommend to wait a bit until this code is a bit more stable.  I'm forced to run MythTV on Feisty because of the architecture of my fe machine ... it's an ASUS P5B-VM with the Jmicron controller that gives problems on 6.10.  I'll be downloading the latest code this weekend and trying a reinstall to see if my problems are related to a beta-level code release (I'm actually not sure of the exact vintage of Feisty I'm running so I'm not about to blame the code until I've eliminated all other possibilities).

Robert.

---

### Post by newlinux on 2007-04-20
I posed a similar question a couple weeks back:
[http://ubuntuforums.org/showthread.php?t=394015](http://ubuntuforums.org/showthread.php?t=394015)

Even though I have a separate partitions for media and recordings, and have nightly backups of all important stuff (home dir files, myth database, media), I'm still going to leave my systems with backends  as edgy (I might be converting another one of my Windows systems to a backend, that will be feisty). For me I want it running 24/7 (I use it almost everyday and everything is as good as I could want it now) and don't want to chance having to redo all the configuring, which is really what took the most time. That said, now that I've done this a few times, I could probably get through it quickly, but I don't want to chance it. I was more worried about being slipping behind in releases when something I really want comes out - but I'll cross that bridge when I get to it, and at that point instead of upgrading a couple distros I'll probably just reinstall...

---

### Post by gapplewagen on 2007-04-23
I did the upgrade today and mythtv is not working.  The backend won't load due to some database issues.  My /var/log/mythtv/mythbackend.log reports this:

```

2007-04-23 23:05:43.519 Database Schema upgrade FAILED, unlocking.
2007-04-23 23:05:43.520 Couldn't upgrade database to new schema
2007-04-23 23:06:03.708 Using runtime prefix = /usr
2007-04-23 23:06:03.728 New DB connection, total: 1
2007-04-23 23:06:03.736 Connected to database 'mythconverg' at host: localhost
2007-04-23 23:06:03.749 Current Schema Version:
2007-04-23 23:06:03.753 Newest Schema Version : 1160
2007-04-23 23:06:03.759 New DB connection, total: 2
2007-04-23 23:06:03.760 Connected to database 'mythconverg' at host: localhost
2007-04-23 23:06:03.762 Setting Lock for Database Schema upgrade. If you see a $
2007-04-23 23:06:03.763 New DB connection, total: 3
2007-04-23 23:06:03.765 Connected to database 'mythconverg' at host: localhost
2007-04-23 23:06:03.768 Told to create a NEW database schema, but the database
already has 76 tables.
If you are sure this is a good mythtv database, verify
that the settings table has the DBSchemaVer variable.

2007-04-23 23:06:03.770 Database Schema upgrade FAILED, unlocking.
2007-04-23 23:06:03.771 Couldn't upgrade database to new schema

```

Still looking for an answer.

---

### Post by gapplewagen on 2007-04-23
Ok I fixed the database issue by repairing the settings table:

```

mysql -u mythtv -pmythtv
use mythconverg;
repair table settings;

```

And that seems to have at least allowed me to start the backend.  I'm still not fully working from this box.  Getting "TV Error: LiveTV not successfully started".

---

### Post by superm1 on 2007-04-23
> **gapplewagen said:**
> Ok I fixed the database issue by repairing the settings table:

```

mysql -u mythtv -pmythtv
use mythconverg;
repair table settings;

```And that seems to have at least allowed me to start the backend.  I'm still not fully working from this box.  Getting "TV Error: LiveTV not successfully started".
Any ideas how this corruption happened in the first place?  I'm wondering here if you have a corrupted mysql table, if perhaps other files on the file system are broke too?

---

### Post by gapplewagen on 2007-04-24
> **superm1 said:**
> Any ideas how this corruption happened in the first place?  I'm wondering here if you have a corrupted mysql table, if perhaps other files on the file system are broke too?

Not sure how it happened.  No errors during install.  I assume that the sql schema update script broke it during it's original run through.  I didn't see any evidence of this though.

---

### Post by superm1 on 2007-04-24
> **gapplewagen said:**
> Not sure how it happened.  No errors during install.  I assume that the sql schema update script broke it during it's original run through.  I didn't see any evidence of this though.

Just as a precaution to rule out corruption on the disk for other myth binaries, I'd say do an inplace reinstall of the packages:

```
 sudo apt-get install --reinstall libmyth-0.20 mythtv-backend mythtv-common mythtv-frontend
```

---

### Post by gapplewagen on 2007-04-24
> **superm1 said:**
> Just as a precaution to rule out corruption on the disk for other myth binaries, I'd say do an inplace reinstall of the packages:

```
 sudo apt-get install --reinstall libmyth-0.20 mythtv-backend mythtv-common mythtv-frontend
```


Thanks I'll give that a try later.

---

### Post by gapplewagen on 2007-04-25
All is fixed on my combined backend/frontend box now.  I just repaired all mysql tables with:

```

mysqlcheck -r mythconverg -umythtv -pmythtv

```

I haven't tested on my frontend only box yet.  Of course I haven't even upgraded that one to Feisty yet.  I wonder if it would work without upgrading it.

---

### Post by gapplewagen on 2007-04-25
Another quick note, it seems to have killed off all of my scheduled recordings.  Search phrases are still there but nothing is scheduled.

---

### Post by gapplewagen on 2007-04-25
> **gapplewagen said:**
> Another quick note, it seems to have killed off all of my scheduled recordings.  Search phrases are still there but nothing is scheduled.

Never mind, they magically came back.

---

### Post by AndrewWalker on 2007-04-26
I've lost my tv card!
Here's my log file, could do without the smartass remark at the end of it though!

2007-04-26 19:29:20.229 Using runtime prefix = /usr
2007-04-26 19:29:20.542 New DB connection, total: 1
2007-04-26 19:29:20.812 Connected to database 'mythconverg' at host: 192.168.0.7
2007-04-26 19:29:21.118 Current Schema Version: 1160
Starting up as the master server.
2007-04-26 19:29:21.532 New DB connection, total: 2
2007-04-26 19:29:21.636 Connected to database 'mythconverg' at host: 192.168.0.7
2007-04-26 19:29:21.701 EITHelper: localtime offset 1:00:00
2007-04-26 19:29:21.948 DVBChan(0) Error: Opening DVB frontend device failed.
                        eno: No such file or directory (2)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?

Any quick fixes or have I got to set everything back up from scratch?

---

### Post by newlinux on 2007-04-26
Do you see your card in mythtv-setup?

---

### Post by gapplewagen on 2007-04-27
> **AndrewWalker said:**
> I've lost my tv card!
Here's my log file, could do without the smartass remark at the end of it though!

2007-04-26 19:29:20.229 Using runtime prefix = /usr
2007-04-26 19:29:20.542 New DB connection, total: 1
2007-04-26 19:29:20.812 Connected to database 'mythconverg' at host: 192.168.0.7
2007-04-26 19:29:21.118 Current Schema Version: 1160
Starting up as the master server.
2007-04-26 19:29:21.532 New DB connection, total: 2
2007-04-26 19:29:21.636 Connected to database 'mythconverg' at host: 192.168.0.7
2007-04-26 19:29:21.701 EITHelper: localtime offset 1:00:00
2007-04-26 19:29:21.948 DVBChan(0) Error: Opening DVB frontend device failed.
                        eno: No such file or directory (2)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?

Any quick fixes or have I got to set everything back up from scratch?

Have you upgraded kernels?  If so did you follow the instructions here:
[https://help.ubuntu.com/community/Install_IVTV_Edgy]("https://help.ubuntu.com/community/Install_IVTV_Edgy")

Specifically this:

```

sudo m-a update,prepare
sudo m-a a-i ivtv
sudo depmod -a
sudo modprobe ivtv

```

---

