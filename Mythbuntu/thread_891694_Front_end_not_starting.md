---
title: "Front end not starting"
date: 2008-08-16
forum: Mythbuntu
---

### Post by bkr1_2k on 2008-08-16
I had my mythbuntu box working well, but then did something and now my front end won't start.  

I had things working well, and for some reason the box crashed.  When I booted again, i had to reconfigure the X server because my S video out wasn't working.  I installed the NVidia driver and got the S video working but now my front end won't start.  It tries for a moment and then reverts to the desktop.

running mythbuntu 8.04 on a P3 933 with 512 of RAM an NVidia video card and two hauppage 150 cards.

---

### Post by funkydan2 on 2008-08-17
Two things you could try.

MythTV logs to /var/log/mythtv/mythfrontend.log so you could have a read of that or you could open up a terminal and run 'mythfrontend' which will give you some output in the terminal window and will hopefully point out what is wrong.

---

### Post by bkr1_2k on 2008-08-17
Thank you for the reply.  Here is the data from my log file, but the only thing I see that I suspect could be the problem is the "QImage null image" or the cdrecord scan failure...  Unfortunately I have no idea how to fix either of those right now, assuming they are the problem.

Starting mythfrontend.real..
2008-08-17 10:13:18.133 New DB connection, total: 2
2008-08-17 10:13:18.134 Connected to database 'mythconverg' at host: localhost
2008-08-17 10:13:18.139 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-08-17 10:13:18.140 Enabled verbose msgs:  important general
2008-08-17 10:13:20.339 Total desktop dim: 1024x768, over 2 screen[s].
2008-08-17 10:13:20.339 Screen 0 dim: 1024x768.
2008-08-17 10:13:20.339 Screen 1 dim: 1024x768.
2008-08-17 10:13:20.339 Primary screen 0.
2008-08-17 10:13:20.341 Using screen 0, 1024x768 at 0,0
2008-08-17 10:13:20.347 Switching to square mode (MythCenter)
2008-08-17 10:13:20.398 Using the Qt painter
2008-08-17 10:13:20.403 lirc init success using configuration file: /home/myth1/
.mythtv/lircrc
2008-08-17 10:13:20.404 JoystickMenuClient Error: Joystick disabled - Failed to 
read /home/myth1/.mythtv/joystickmenurc
QImage::smoothScale: Image is a null image
2008-08-17 10:13:23.212 Loading from: /usr/share/mythtv/themes/MythCenter/base.x
ml
2008-08-17 10:13:23.523 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-08-17 10:13:23.826 Registering Internal as a media playback plugin.
2008-08-17 10:13:24.138 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-08-17 10:13:24.574 Failed to run 'cdrecord --scanbus'
2008-08-17 10:13:24.581 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-08-17 10:13:24.590 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-08-17 10:13:24.718 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address xxx.xxx.xxx.xxx:5060 NAT address xxx.xxx.xxx.xxx
SIP: Cannot register; proxy, username or password not set
2008-08-17 10:13:25.328 Starting update of NWS-XML
2008-08-17 10:13:25.341 Starting update of NDFD-6_day

---

