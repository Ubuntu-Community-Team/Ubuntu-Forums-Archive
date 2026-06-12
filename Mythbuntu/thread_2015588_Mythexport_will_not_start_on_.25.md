---
title: "Mythexport will not start on .25"
date: 2012-07-03
forum: Mythbuntu
---

### Post by n8tgc on 2012-07-03
Previously was running Mythbuntu 11.04 and Mythexport ran perfectly.
 
However...
 
Upgraded to a clean install of Mythbuntu 12.04. Everything is running great EXCEPT for Mythexport. When I start Mythexport manually I get an "Ok"
 
sudo /etc/init.d/mythexport start
* Starting MythExport Daemon: mythexport [ OK ]
 
Then if I check status....
 
sudo /etc/init.d/mythexport status
* mythexport is not running
 
When I kick off a User Job from Mythtv I get this...
 
ps -ef|grep mythe
mythtv 17265 17045 0 15:18 ? 00:00:00 sh -c mythexport_addjob starttime=20120703120000 chanid=1042 config=PortableH264HighRes deleteperiod= podcastname=
mythtv 17266 17265 1 15:18 ? 00:00:00 /usr/bin/perl /usr/bin/mythexport_addjob starttime=20120703120000 chanid=1042 config=PortableH264HighRes deleteperiod= podcastname=
 
Also, I have no mythexport.log in /var/log/mythtv 
 
If I manually create the log file, the results remain the same. FWIW, I installed Mythexport as a part of the Mythbuntu 12.04 installer.
 
I have tried adding debug to the AGRS variable in /etc/init.d/mythexport but I still get no logs, nor does the daemon start.
 
Any suggestions? What am I missing to get Mythexport to start-up?

---

### Post by jim09 on 2012-07-08
Im getting the same thing.  I installed it later from  the MCC panel and I'm pretty sure that there were dependancy problems with the install in the details section.

---

### Post by n8tgc on 2012-07-09
[SIZE=3][FONT=Calibri]Found the issue that was plaguing my machine. After creating the mythexport.log file in /var/log/mythtv , I had to modify the permissions. All the other logs in the folder have permissions of 644. I changed mythexport.log to 666 (see below…) and everything started working as expected.[/FONT][/SIZE]

[SIZE=3][FONT=Calibri]-rw-r--r-- 1 syslog adm 0 Jul 2 08:06 mythccextractor.log[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]-rw-r--r-- 1 syslog adm 127616 Jul 9 03:38 mythcommflag.log[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]-rw-rw-rw- 1 syslog adm 7510101 Jul 9 12:48 mythexport.log[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]-rw-r--r-- 1 syslog adm 145900 Jul 8 07:27 mythfilldatabase.log[/FONT][/SIZE]
 
 
[SIZE=3][FONT=Calibri]Jim09, hope this helps you![/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]~Christian[/FONT][/SIZE]

---

### Post by jim09 on 2012-07-09
Thanks Christian, it worked for me 2.:)

---

### Post by ijumpship on 2012-07-13
This post maybe a life saver.I hope

Okay I am a developer of set-top boxes an Smart TV apps.
I am developing an app that will use RSS. Feeds so far all the coding for the app works,I poke around and found Mythexport and Mythpodcaster.

I want to use Mythexport as it just plug and play.and I install it via MCC.
Mythpodcaster require compiling etc.which I cannot afford my box to break now.

Here are my question.

[B](1) I use Ubuntu 11.10 (Oneiric Ocelot).I want to use the both live tv and  mythvideo *(/var/lib/mythtv/video) as a symlink.Are any of you doing this? I want to be able to put my videos on the feeds
[/B]
[B](2)Is mythexport supported beyond mythtv 0.24? 
[/B]
Might sound a bit lazy but I am on about 3 projects and I have limited time so if I clear a few answerI can dive in knowing that any problem is on my side.

Thanks much

---

### Post by n8tgc on 2012-07-13
I can't respond to your first question. I've not dealt with the symlink functionality in mythexport.
 
To your second question... Yes, mythexport performs well on mythtv .25. I am running it on Mythbuntu 12.04 without issues.

---

### Post by androidoc on 2012-10-28
I am experiencing the same issue with mythexport.

Mythweb works.
Mythexport gives me the same error: Internal server Error. 

I when I looked in log folder there was no mythexport log so I created a blank one with gedit and copied the permissions from one of other logs in that folder.

As the original poster did, I can launch mythexport manually but its status is reported as not started when I check. 

Did I miss a step or do I have a different problem altogether?

This is a new installation for me and I'm a new mythtv user, only for a few weeks.  Be kind.

Thanks

---

