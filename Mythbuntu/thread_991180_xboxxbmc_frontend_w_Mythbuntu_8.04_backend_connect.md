---
title: "xbox/xbmc frontend w/ Mythbuntu 8.04 backend connection problems"
date: 2008-11-23
forum: Mythbuntu
---

### Post by jtpiano on 2008-11-23
Hi everyone,
I built a backend server using version 8.04 of Mythbuntu.  I am able to successfully connect using the live cd version of Mythbuntu as a frontend.  I did a quick test of watching live tv and scheduling a recording.  It seems to be working correctly.  If I try to use my xbox as a frontend, it doesn't connect, I receive the following error message: "Failed to connect to MySQL Database 'conn'".  What logs should I be checking to help figure this out?  I am using xbmc version 0.20.34b.  The one item I am not sure of is the setting for protocol version in xbmc.  The default is 30.  I have tried changing it to 29 and 31 with no luck.  Your input is appreciated.  Thanks in advance for your help!!!  :)

---

### Post by volkswagner on 2008-11-23
You will find the logs in /var/log/mythtv/mythbackend.log and and also /var/log/mythtv/mythfrontend.log

You will want to check the backend log on the master machine.

If you are talking about the protocol version for myth, it should be 40.

If you open a terminal on the backend enter the following, then try to start you xbox.

```
tail -f /var/log/mythtv/mythbackend.log
``` 

There is also a check box in the backend setup to allow xbox hardware.

---

### Post by jtpiano on 2008-11-23
>>>There is also a check box in the backend setup to allow xbox hardware.>>>

Where is the check box?  I must have overlooked it.

---

### Post by jtpiano on 2008-11-23
Here are my logs.  

~$ tail -f /var/log/mythtv/mythtvbackend.log
Reading state information... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading package lists... Done
building dependency tree       
Reading state information... Done
2008-11-23 12:39:34.640 Connecting to backend server: 192.168.1.4:6543 (try 1 of 5)
2008-11-23 12:39:34.643 Using protocol version 40
2008-11-23 12:39:38.836 Deleting UPnP client...

~$ tail -f /var/log/mythtv/mythtvfrontend.log
2008-11-23 17:44:19.373 HDHRChan(ffffffff/0): device found at address 192.168.1.14
2008-11-23 17:47:59.319 HDHRChan(ffffffff/1): device found at address 192.168.1.14
2008-11-23 17:49:14.711 Reschedule requested for id -1.
2008-11-23 17:49:14.762 Scheduled 2 items in 0.0 = 0.02 match + 0.03 place
2008-11-23 17:49:45.589 HDHRChan(ffffffff/0): device found at address 192.168.1.14
2008-11-23 17:50:02.099 MainServer::HandleAnnounce Monitor
2008-11-23 17:50:02.105 adding: mythbuntube as a client (events: 0)
2008-11-23 17:51:29.469 MainServer::HandleVersion - Client speaks protocol version 34 but we speak 40!
2008-11-23 17:51:29.524 MainServer::HandleAnnounce Monitor
2008-11-23 17:51:29.525 adding: 192.168.1.15 as a client (events: 0)

It appears there is a mismatch between protocol versions (and so the frontend and backend can't talk to each other).  I guess I'll have to see if the frontend can be upgraded or downgrade the backend.

---

### Post by jtpiano on 2008-11-23
Ooops! I have the labels for frontend and backend wrong.  They should be flipped.

---

### Post by perhagge on 2008-11-24
I guess that you use the XBMC mythtv script ?
I have same setup as you, I found following solution: [http://sourceforge.net/forum/forum.php?thread_id=1738450&forum_id=436331](http://sourceforge.net/forum/forum.php?thread_id=1738450&forum_id=436331)

I also now found this that I will try later:
[http://xbmc.org/forum/showpost.php?p=233836&postcount=4](http://xbmc.org/forum/showpost.php?p=233836&postcount=4)

I have tried the script without any greater success, however XBMC is great to watch allready recorded shows, but then I connect by UPNP. 

I'm also interested where to find the xbox check box!

/Pär

---

### Post by volkswagner on 2008-11-24
> **jtpiano said:**
> >>>There is also a check box in the backend setup to allow xbox hardware.>>>

Where is the check box?  I must have overlooked it.

Umm, just found it.  Sorry for the confusion.  

It is in the frontend general settings.  I'm not sure how to get a frontend going on an Xbox.

---

### Post by jtpiano on 2008-11-25
:)!!!*PROBLEM RESOLVED*!!!:)

My problem was two tiered:
#1
After finding out from the logs that protocol version mismatch was happening I updated to the latest version of the xbmc mythtv script out of CVS today.  This brought me up to version 40 of the protocol. I tried this and still couldn't connect. (Though the types of error messages I was seeing did change some.)

#2
I made a change in MySQL
mysql -u root -p 
SET PASSWORD for mythtv = OLD_PASSWORD('mythtv'); 
- where ‘mythtv’ is the password that is configured in the MythTV settings on the XBox.  Presto! All done.

It's working very nicely now.  I have some minor tweaking to do but that shouldn't be too big a deal.... (knock on wood)  Thanks for your help Volkswagner.  You set me on the right track.  I learned Linux in school but Myth is certainly an animal of a different color.

---

### Post by jtpiano on 2008-11-25
You are on the right track.  I did look at the links you included.  I found out quickly that not all commands work.  You know how computers are- GIGO (syntax is everything).  If you are using the same backend as me then what I listed should work for you too.  BTW, the frontend will allow you to record.  Although I am running an SMB share not UPnP.  Hope this helps.

---

### Post by tgm4883 on 2008-11-25
MythTV support is built into the current xbmc (has been for months now)  

You need to add a video source like this

```
myth://mythtv:password@192.168.1.116
```

See [http://www.mythtv.org/wiki/index.php/Xbox_Frontend#Running_XBMC_with_native_MythTV_Support](http://www.mythtv.org/wiki/index.php/Xbox_Frontend#Running_XBMC_with_native_MythTV_Support) for more info.

---

### Post by perhagge on 2008-11-25
I have also tried the myth:// protocol but I cant get live tv working. I can connect and find the menu, but live tv wont start. 

Are there any one else getting it to work? That is the missing part for my "perfect" mythtv set-up, today I schedule recordings from mythweb, and use the xbox to view recorded movies. In general this is enough for me and the family, but it would be great to watch live tv, pausing and manage the recordings from the soffa.

I have a dedicated backend with mythbuntu 8.04, nova 500-T dual tuner (DVB-T), AMD am2 X2 4200, 2 Gb memory and 500 Gb HD. 
For the frontend I have xbmc, and try at least every month to upgrade to latest t3ch updates. It all connects trough a dlink 604.

With the xbmc myth script I can get live tv start but it is very slow starting and I cant change channel. It also occupies one of the tuners after leaving the script and shutting down the xbox. Then I need to reboot the backend.

/Pär

---

### Post by jtpiano on 2008-11-25
> **tgm4883 said:**
> MythTV support is built into the current xbmc (has been for months now)  

You need to add a video source like this

```
myth://mythtv:password@192.168.1.116
```

See [http://www.mythtv.org/wiki/index.php/Xbox_Frontend#Running_XBMC_with_native_MythTV_Support](http://www.mythtv.org/wiki/index.php/Xbox_Frontend#Running_XBMC_with_native_MythTV_Support) for more info.


Thanks for the tip!  I am just getting up to speed on the different options available for XBMC.

---

### Post by jtpiano on 2008-11-25
> **perhagge said:**
> I have also tried the myth:// protocol but I cant get live tv working. I can connect and find the menu, but live tv wont start. 

Are there any one else getting it to work? That is the missing part for my "perfect" mythtv set-up, today I schedule recordings from mythweb, and use the xbox to view recorded movies. 

/Pär

Perhaps you can describe in further details the options you chose when you setup your backend?  I know my live tv is working without any real fuss.

---

