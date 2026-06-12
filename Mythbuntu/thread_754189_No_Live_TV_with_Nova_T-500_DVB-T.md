---
title: "No Live TV with Nova T-500 DVB-T"
date: 2008-04-13
forum: Mythbuntu
---

### Post by Teamgeist on 2008-04-13
Hi everyone.

I have a problem with my Hauppauge Nova t-500 and watching Live TV.
This is on Mythbuntu 8.04 installed today.
It simply does not work.
Under System Information insinde Mythfrontend it says Tuner1 and Tuner2 not available. Even though I already did a scan for programms during Mythbackend configuration.

When started from the Terminal it gives me the following:

```
tv@tv:~$ mythtv
2008-04-13 20:32:46.119 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-13 20:32:46.137 XScreenSaver support enabled
2008-04-13 20:32:46.138 DPMS is active.
2008-04-13 20:32:46.139 Using localhost value of tv-test
2008-04-13 20:32:46.171 New DB connection, total: 1
2008-04-13 20:32:46.178 Connected to database 'mythconverg' at host: localhost
2008-04-13 20:32:46.180 Closing DB connection named 'DBManager0'
2008-04-13 20:32:46.182 Primary screen 0.
2008-04-13 20:32:46.183 Connected to database 'mythconverg' at host: localhost
2008-04-13 20:32:46.185 Using screen 0, 1280x768 at 0,0
2008-04-13 20:32:46.243 max_width: 1280 max_height: 800
2008-04-13 20:32:46.246 Primary screen 0.
2008-04-13 20:32:46.247 Using screen 0, 1280x768 at 0,0
2008-04-13 20:32:46.302 Switching to square mode (Mythbuntu-8.04)
2008-04-13 20:32:46.354 Using the OpenGL painter
mythtv: could not connect to socket
mythtv: Connection refused
2008-04-13 20:32:46.355 lirc_init failed for mythtv, see preceding messages
2008-04-13 20:32:46.355 JoystickMenuClient Error: Joystick disabled - Failed to read /home/tv/.mythtv/joystickmenurc
2008-04-13 20:32:47.382 New DB connection, total: 2
2008-04-13 20:32:47.383 Connected to database 'mythconverg' at host: localhost
2008-04-13 20:32:47.440 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-04-13 20:32:47.441 Using protocol version 40
2008-04-13 20:32:47.460 TV Error: Failed to get recording show list
tv@tv:~$ 
```

Nothing happens from there.

When trying to start mythfrontend from Terminal it gives me the following:
```
tv@tv:~$ mythfrontend
2008-04-13 20:34:50.901 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-13 20:34:50.904 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-04-13 20:34:50.905 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-04-13 20:34:50.922 XScreenSaver support enabled
2008-04-13 20:34:50.923 DPMS is active.
2008-04-13 20:34:50.924 Using localhost value of tv-test
2008-04-13 20:34:50.944 New DB connection, total: 1
2008-04-13 20:34:50.951 Connected to database 'mythconverg' at host: localhost
2008-04-13 20:34:50.954 Closing DB connection named 'DBManager0'
2008-04-13 20:34:50.956 Primary screen 0.
2008-04-13 20:34:50.957 Connected to database 'mythconverg' at host: localhost
2008-04-13 20:34:50.959 Using screen 0, 1280x768 at 0,0
2008-04-13 20:34:50.971 New DB connection, total: 2
2008-04-13 20:34:50.972 Connected to database 'mythconverg' at host: localhost
2008-04-13 20:34:50.976 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-04-13 20:34:50.976 Enabled verbose msgs:  important general
2008-04-13 20:34:51.104 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-04-13 20:34:51.119 Unable to parse themeinfo.xml for glass-wide
2008-04-13 20:34:51.119 The theme (glass-wide) is missing a themeinfo.xml file
2008-04-13 20:34:51.371 Unable to parse themeinfo.xml for glass-wide
2008-04-13 20:34:51.371 The theme (glass-wide) is missing a themeinfo.xml file
2008-04-13 20:34:51.769 Primary screen 0.
2008-04-13 20:34:51.769 Using screen 0, 1280x768 at 0,0
2008-04-13 20:34:51.773 Switching to square mode (Mythbuntu-8.04)
2008-04-13 20:34:51.826 Using the OpenGL painter
mythtv: could not connect to socket
mythtv: Connection refused
2008-04-13 20:34:51.827 lirc_init failed for mythtv, see preceding messages
2008-04-13 20:34:51.828 JoystickMenuClient Error: Joystick disabled - Failed to read /home/tv/.mythtv/joystickmenurc
2008-04-13 20:34:53.691 Specified base font 'medium' does not exist for font clock
2008-04-13 20:34:53.692 Specified base font 'medium' does not exist for font small
2008-04-13 20:34:53.692 Specified base font 'medium' does not exist for font medium
2008-04-13 20:34:53.692 Specified base font 'medium' does not exist for font large
2008-04-13 20:34:53.694 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-04-13 20:34:53.749 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-04-13 20:34:53.824 Registering Internal as a media playback plugin.
2008-04-13 20:34:53.970 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-04-13 20:34:54.050 Failed to run 'cdrecord --scanbus'
2008-04-13 20:34:54.068 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-04-13 20:34:54.075 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-04-13 20:34:54.153 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-04-13 20:34:55.473 Using NV NPOT texture extension
2008-04-13 20:34:57.396 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-04-13 20:34:57.397 Using protocol version 40
2008-04-13 20:35:02.381 Deleting UPnP client...
2008-04-13 20:35:02.382 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
tv@tv:~$ 

```

Mythfrontend starts just fine, but watching Live TV does not work.

Any suggestions?

---

### Post by stevanbt on 2008-04-14
Hi,
What do you get when you type this in the terminal:-

```
dmesg | grep -i dvb
```


This will confirm if the card has been installed correctly.

Thanks, Steve.

---

### Post by Teamgeist on 2008-04-14
Here you go:

```
tv@tv:~$ dmesg | grep -i dvb
[   32.664629] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   33.310655] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   34.015486] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   34.015540] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   34.015989] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   34.129009] DVB: registering frontend 0 (DiBcom 3000MC/P)...
[   34.641950] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   34.642147] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   34.648071] DVB: registering frontend 1 (DiBcom 3000MC/P)...
[   35.207279] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:10.0/0000:01:09.2/usb5/5-1/input/input5
[   35.242889] dvb-usb: schedule remote query interval to 150 msecs.
[   35.242897] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   35.243057] usbcore: registered new interface driver dvb_usb_dib0700
```

Seems fine to me...

---

### Post by stevanbt on 2008-04-14
Ok, so it looks like the card is recognised correctly.  Have you setup a storage group for live TV?

---

### Post by Teamgeist on 2008-04-15
After trying really anything to get this sucker working I figured I would just reinstall the whole system.

Now everything works like expected.
Thanks a lot for your help and effort stevanbt!

---

