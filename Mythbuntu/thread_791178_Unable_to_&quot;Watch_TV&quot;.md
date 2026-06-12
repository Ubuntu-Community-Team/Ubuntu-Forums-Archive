---
title: "Unable to &quot;Watch TV&quot;"
date: 2008-05-11
forum: Mythbuntu
---

### Post by ldgriffin on 2008-05-11
I installed a fresh copy of the Mythbuntu 8.04 today and went through all of the updates etc.  And I still cannot watch tv.  the Mythfrontend loads fine and allows me to run through every menu option and setting except for the actual "Watch TV", which immediately kills the frontend and sends me to the desktop.  Based on the mythfrontend.log file there seems to an invalid entry for my sound card.  The log ends with the following: Check Mixer Name in Setup: '/dev/mixer', unfortunatly I can't find anyplace in the setup to specify the audio device.  the sound works fine from the desktop using apps like vlc, miro, etc.

Here's the log file text:


Starting mythfrontend.real..
2008-05-11 23:20:07.058 New DB connection, total: 2
2008-05-11 23:20:07.059 Connected to database 'mythconverg' at host: localhost
2008-05-11 23:20:07.062 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-05-11 23:20:07.062 Enabled verbose msgs:  important general
2008-05-11 23:20:07.171 Unable to parse themeinfo.xml for glass-wide
2008-05-11 23:20:07.171 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-11 23:20:07.366 Unable to parse themeinfo.xml for glass-wide
2008-05-11 23:20:07.367 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-11 23:20:08.728 Primary screen 0.
2008-05-11 23:20:08.729 Using screen 0, 1024x768 at 0,0
2008-05-11 23:20:08.731 Switching to square mode (Mythbuntu-8.04)
2008-05-11 23:20:08.757 Using the Qt painter
mythtv: could not connect to socket
mythtv: Connection refused
2008-05-11 23:20:08.758 lirc_init failed for mythtv, see preceding messages
2008-05-11 23:20:08.758 JoystickMenuClient Error: Joystick disabled - Failed to read /home/lynn/.mythtv/joystickmenurc
2008-05-11 23:20:10.921 Specified base font 'medium' does not exist for font clock
2008-05-11 23:20:10.922 Specified base font 'medium' does not exist for font small
2008-05-11 23:20:10.922 Specified base font 'medium' does not exist for font medium
2008-05-11 23:20:10.922 Specified base font 'medium' does not exist for font large
2008-05-11 23:20:10.924 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-05-11 23:20:11.136 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-05-11 23:20:11.196 Registering Internal as a media playback plugin.
2008-05-11 23:20:11.326 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-05-11 23:20:11.384 Failed to run 'cdrecord --scanbus'
2008-05-11 23:20:11.397 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-05-11 23:20:11.400 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-05-11 23:20:11.449 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.0.151:5060 NAT address 192.168.0.151
SIP: Cannot register; proxy, username or password not set
2008-05-11 23:20:18.260 Connecting to backend server: 192.168.0.151:6543 (try 1 of 5)
2008-05-11 23:20:18.261 Using protocol version 40
2008-05-11 23:20:18.294 TV: Attempting to change from None to WatchingLiveTV
2008-05-11 23:20:18.295 Using protocol version 40
2008-05-11 23:20:20.605 New DB connection, total: 3
2008-05-11 23:20:20.606 Connected to database 'mythconverg' at host: localhost
2008-05-11 23:20:21.362 AFD: Opened codec 0x83e3640, id(MPEG2VIDEO) type(Video)
2008-05-11 23:20:21.362 AFD: codec MP2 has 2 channels
2008-05-11 23:20:21.363 AFD: Opened codec 0x83e39c0, id(MP2) type(Audio)
2008-05-11 23:20:21.486 Opening audio device 'default'. ch 2(2) sr 48000
2008-05-11 23:20:21.487 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-05-11 23:20:21.497 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'


Thanks in advance for your help

---

### Post by volkswagner on 2008-05-12
Sound setup is in...Setup>setup/config>General settings, page 3.

---

### Post by ldgriffin on 2008-05-12
Thanks for the reply.  I don't know how I didn't see that.  I guess that goes to show you shouldn't work on this stuff too late at night.

Unfortunatly, I still can't watch tv.  The output now just ends with segmentation fault and kicks back to the desktop.  I'm not sure what a segmentation fault is, but any further help the community can provide is greatly appreciated.  Here's the end of the terminal output from the mythfrontend:

2008-05-12 13:50:08.064 AFD: Opened codec 0x83e9020, id(MPEG2VIDEO) type(Video)
2008-05-12 13:50:08.064 AFD: codec MP2 has 2 channels
2008-05-12 13:50:08.064 AFD: Opened codec 0x83e5a90, id(MP2) type(Audio)
2008-05-12 13:50:08.185 Opening audio device 'default'. ch 2(2) sr 48000
2008-05-12 13:50:08.186 Opening ALSA audio device 'default'.
Segmentation fault


This is where it closes the frontend and I end up looking at the desktop.

---

### Post by OffAxis on 2008-05-13
Does sound work outside of mythtv?
Like with VLC or mplayer?

Try this:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by ldgriffin on 2008-05-16
this was a new install from the mythbuntu 8.04 cd.  Any way the sound works fine from other applications.  I was able to setup a recording from the frontend and open the video file from the desktop and it has sound.  My sound card is an older SB Live 5.1 and the tuner cards I use are (1) hauppage 150 and (1) hauppage mce500.  I've searched the forums nd I haven't found anything about an incompatibility but who knows.

---

