---
title: "Front end wont work"
date: 2008-11-29
forum: Mythbuntu
---

### Post by darkhammer8108 on 2008-11-29
im just installed ubuntu 8.10 and installed the mythtv meta package. im using a hauppauge hvr 1600. i got the back end running and i scanned for the channels fine using schedules direct. when i run the mythfrontend though and go to watch tv it tries to go into it and then drops me back on the home screen. no error messages in the console output from the front end that i can tell. 

My Output
```
2008-11-29 18:03:28.040 Using runtime prefix = /usr
2008-11-29 18:03:28.217 XScreenSaver support enabled
2008-11-29 18:03:28.217 DPMS is active.
2008-11-29 18:03:28.218 Empty LocalHostName.
2008-11-29 18:03:28.218 Using localhost value of darkhammer
2008-11-29 18:03:28.224 New DB connection, total: 1
2008-11-29 18:03:28.228 Connected to database 'mythconverg' at host: localhost
2008-11-29 18:03:28.229 Closing DB connection named 'DBManager0'
2008-11-29 18:03:28.234 Total desktop dim: 2960x1050, over 2 screen[s].
2008-11-29 18:03:28.234 Screen 0 dim: 1680x1050.
2008-11-29 18:03:28.234 Screen 1 dim: 1280x1024.
2008-11-29 18:03:28.234 Primary screen 0.
2008-11-29 18:03:28.235 Connected to database 'mythconverg' at host: localhost
2008-11-29 18:03:28.235 Using screen 0, 1680x1050 at 0,0
2008-11-29 18:03:28.241 New DB connection, total: 2
2008-11-29 18:03:28.241 Connected to database 'mythconverg' at host: localhost
2008-11-29 18:03:28.243 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-11-29 18:03:28.243 Enabled verbose msgs:  important general
DisplaResX: Unable to XRRgetScreenInfo
DisplaResX: Unable to XRRgetScreenInfo
2008-11-29 18:03:28.557 No theme dir: /home/shaun/.mythtv/themes/neon-wide
2008-11-29 18:03:28.558 Total desktop dim: 2960x1050, over 2 screen[s].
2008-11-29 18:03:28.558 Screen 0 dim: 1680x1050.
2008-11-29 18:03:28.558 Screen 1 dim: 1280x1024.
2008-11-29 18:03:28.558 Primary screen 0.
2008-11-29 18:03:28.559 Using screen 0, 1680x1050 at 0,0
2008-11-29 18:03:28.559 No theme dir: /home/shaun/.mythtv/themes/neon-wide
2008-11-29 18:03:28.559 Switching to wide mode (neon-wide)
2008-11-29 18:03:28.577 Using the Qt painter
2008-11-29 18:03:28.578 JoystickMenuClient Error: Joystick disabled - Failed to read /home/shaun/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: Connection refused
2008-11-29 18:03:28.578 lirc_init failed for mythtv, see preceding messages
2008-11-29 18:03:29.397 Specified base font 'medium' does not exist for font clock
2008-11-29 18:03:29.398 Specified base font 'medium' does not exist for font small
2008-11-29 18:03:29.398 Specified base font 'medium' does not exist for font medium
2008-11-29 18:03:29.398 Specified base font 'medium' does not exist for font large
2008-11-29 18:03:29.399 Loading from: /usr/share/mythtv/themes/neon-wide/base.xml
2008-11-29 18:03:29.472 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-29 18:03:29.506 Registering Internal as a media playback plugin.
2008-11-29 18:03:29.597 No theme dir: /home/shaun/.mythtv/themes/neon-wide
**THIS IS THE PART WHERE I GO TO "Watch TV"**
2008-11-29 18:03:31.178 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-11-29 18:03:31.179 Using protocol version 40
2008-11-29 18:03:32.417 Deleting UPnP client...

```

how do i get the frontend to work for the tv?

---

### Post by darkhammer8108 on 2008-11-30
new update. it seems to be directly related to the tuner driver now. i tried installing xawtv and running 
```
xawtv /dev/video0
```
and then set my 'c' button to comedy central channel 38. xawtv will not bring up any channels either. to get the channel scanner in mythtv to work before i had to run modprobe -r cx18 and then modprobe cx18 to get the device to load up "properly". after that channel scanner for myth worked but the viewing still doesn't. 
i also tried isntalling the firmware files in the /lib/firmware/2.6.27-9-generic but that didn't seem to make a difference either. 

any thoughts? im not really sure why this card wont show me channels.

---

