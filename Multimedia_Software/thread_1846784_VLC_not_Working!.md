---
title: "VLC not Working!"
date: 2011-09-19
forum: Multimedia Software
---

### Post by montonec on 2011-09-19
Please someone help me... I was editing the configuration files for VLC in order to use an Android application as a remote control. Not only I didn't manage to use it, but the next time I wanted to run VLC nothing happened... I called VLC from the terminal and I got this error message:


VLC media player 1.1.9 The Luggage (revision exported)
[0x93e39ec] main interface: creating httpd
[0x93e39ec] main interface error: socket bind error (Permission denied)
[0x93e39ec] main interface error: socket bind error (Permission denied)
[0x93e39ec] main interface error: cannot create socket(s) for HTTP host
[0x93e39ec] oldhttp interface error: cannot listen on :8080
[0x93e39ec] main interface error: no suitable interface module
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x93c4904] main interface: creating httpd
[0x93c4904] main interface error: socket bind error (Permission denied)
[0x93c4904] main interface error: socket bind error (Permission denied)
[0x93c4904] main interface error: cannot create socket(s) for HTTP host
[0x93c4904] oldhttp interface error: cannot listen on :8080
[0x93c4904] main interface error: no suitable interface module
[0x9313164] main libvlc error: interface "default" initialization failed

I've tried to unisntall it and install it again, deleting all the packets from synaptic, but there's no way... I need VLC because is the only media player I could use to see videos as Banshee and Rythmbox have never worked since 11.04 upgrade....

Help please!

---

### Post by zadehas on 2011-09-19
Have you tried also deleting the config files in your home directory (the ones you edited?)

Mine, for instance, are located in ~/.config/vlc

---

### Post by gordie69 on 2011-09-19
try the software center

---

### Post by gordie69 on 2011-09-19
vlc usually works on all distro os

---

### Post by montonec on 2011-10-06
Thank you all.

Finally I reinstalled Ubuntu and everything seems to work fine now.

---

### Post by mörgæs on 2011-10-06
Good, then please mark the thread 'solved'.

---

