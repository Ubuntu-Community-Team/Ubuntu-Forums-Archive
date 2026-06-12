---
title: "MythTV Watch TV fails"
date: 2009-04-11
forum: Multimedia Software
---

### Post by phil34 on 2009-04-11
Hey guys,

This is my first post on the forums for the first problem I haven't been able to remedy with searching.

I have set up MythTV and after I load the frontend and select watch tv from the main menu it just flashes a black screen very quickly and comes back to the main menu. Here is the section of terminal with the error message.

2009-04-11 20:28:31.298 MSqlQuery: SELECT chanid, starttime, endtime, discontinuity, chainpos, hostprefix, cardtype, channame, input FROM tvchain WHERE chainid = 'live-phil-desktop-2009-04-11T20:28:31' ORDER BY chainpos;
2009-04-11 20:28:31.298 GetEntryAt(-1) failed.
2009-04-11 20:28:31.298 MSqlQuery: SELECT recorded.chanid,starttime,endtime,title, subtitle,description,channel.channum, channel.callsign,channel.name,channel.commmethod, channel.outputfilters,seriesid,programid,filesize, lastmodified,stars,previouslyshown,originalairdate, hostname,recordid,transcoder,playgroup, recorded.recpriority,progstart,progend,basename,recgroup, storagegroup FROM recorded LEFT JOIN channel ON recorded.chanid = channel.chanid WHERE recorded.chanid = '0' AND starttime = '1969-12-31T19:00:00' ;
2009-04-11 20:28:31.298 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2009-04-11 20:28:31.298 TV Error: LiveTV not successfully started
2009-04-11 20:28:31.298 MythSocket(1075d00:38): DownRef: -1
2009-04-11 20:28:31.298 MythSocket(1075d00:38): state change Connected -> Idle
2009-04-11 20:28:31.298 MythSocket(1075d00:-1): delete socket
2009-04-11 20:28:31.298 TV Error: LiveTV not successfully started
2009-04-11 20:28:31.349 TV: Deleting TV Chain in destructor
2009-04-11 20:28:31.349 MSqlQuery: DELETE FROM tvchain WHERE chainid = 'live-phil-desktop-2009-04-11T20:28:31' ;
2009-04-11 20:28:31.349 MythEvent: PLAYBACK_END phil-desktop
2009-04-11 20:28:31.351 DPMS Deactivated 

Please help. Thanks

---

### Post by phil34 on 2009-04-12
Here is the entire error message... Please help I've been working on this all night.

phil@phil-desktop:~$ mythfrontend
2009-04-12 01:01:22.562 Using runtime prefix = /usr
2009-04-12 01:01:22.735 XScreenSaver support enabled
2009-04-12 01:01:22.735 DPMS is active.
2009-04-12 01:01:22.736 Empty LocalHostName.
2009-04-12 01:01:22.736 Using localhost value of phil-desktop
2009-04-12 01:01:22.740 New DB connection, total: 1
2009-04-12 01:01:22.743 Connected to database 'mythconverg' at host: localhost
2009-04-12 01:01:22.744 Closing DB connection named 'DBManager0'
2009-04-12 01:01:22.745 Primary screen 0.
2009-04-12 01:01:22.745 Connected to database 'mythconverg' at host: localhost
2009-04-12 01:01:22.745 Using screen 0, 1680x1050 at 0,0
2009-04-12 01:01:22.749 New DB connection, total: 2
2009-04-12 01:01:22.749 Connected to database 'mythconverg' at host: localhost
2009-04-12 01:01:22.750 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-04-12 01:01:22.750 Enabled verbose msgs:  important general
2009-04-12 01:01:22.916 No theme dir: /home/phil/.mythtv/themes/Retro
2009-04-12 01:01:22.917 Primary screen 0.
2009-04-12 01:01:22.917 Using screen 0, 1680x1050 at 0,0
2009-04-12 01:01:22.917 No theme dir: /home/phil/.mythtv/themes/Retro
2009-04-12 01:01:22.918 Switching to square mode (Retro)
2009-04-12 01:01:22.928 Using the OpenGL painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-04-12 01:01:22.929 lirc_init failed for mythtv, see preceding messages
2009-04-12 01:01:22.929 JoystickMenuClient Error: Joystick disabled - Failed to read /home/phil/.mythtv/joystickmenurc
2009-04-12 01:01:23.540 Loading from: /usr/share/mythtv/themes/Retro/base.xml
2009-04-12 01:01:23.570 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-04-12 01:01:23.586 Registering Internal as a media playback plugin.
2009-04-12 01:01:23.630 No theme dir: /home/phil/.mythtv/themes/Retro
2009-04-12 01:01:24.313 Using NV NPOT texture extension
2009-04-12 01:01:24.948 Connecting to backend server: 192.168.1.9:6543 (try 1 of 5)
2009-04-12 01:01:24.949 Using protocol version 40
2009-04-12 01:01:24.978 TV: Attempting to change from None to WatchingLiveTV
2009-04-12 01:01:24.979 Using protocol version 40
2009-04-12 01:01:25.045 GetEntryAt(-1) failed.
2009-04-12 01:01:25.045 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2009-04-12 01:01:25.045 TV Error: LiveTV not successfully started
2009-04-12 01:01:25.045 TV Error: LiveTV not successfully started
2009-04-12 01:01:25.081 TV: Deleting TV Chain in destructor
2009-04-12 01:01:25.083 DPMS Deactivated 
2009-04-12 01:01:25.084 DPMS Reactivated.
2009-04-12 01:01:26.916 Deleting UPnP client...

---

### Post by phil34 on 2009-04-16
Bump... I am about ready to pay someone if they can fix my problem

---

### Post by de1ta on 2009-04-18
Think I got the same problem. I'm totally new to Mythtv and pretty new to Linux environment. I have installed and setup Mythtv. Manage to find some satellite channels with my DVB-S card. This is my second day trying to get this to work and I am getting closer and closer....I think. 

When o go into the frontend and choose to watch TV I just get a blank screen for 1 sec and then I get back to the main menu again.

Anyone got a clue what could be wrong?

---

### Post by wolfen69 on 2009-04-18
during setup, if you don not choose the right modules, it will not work. go to settings and do the setup over again. when you see the video4linux modules, use the pull down menu to choose another one. for my hauppauge card i need to choose ivtv drivers. if i don't change it, it does not work.

do
```
lspci
```
to show what kind of card you have.

---

