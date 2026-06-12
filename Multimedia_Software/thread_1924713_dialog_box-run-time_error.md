---
title: "dialog box-run-time error"
date: 2012-02-13
forum: Multimedia Software
---

### Post by ajayzizou on 2012-02-13
hello,
i'm writing a code for a dialog-box pop up when a mouse button  is clicked,i got no errors while compiling,while running vlc i got the  following error.


developer@developer-desktop:~/Desktop/vlc-1.1.13$ ./vlc
VLC media player 1.1.13 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x8334764] main interface error: no suitable interface module
[0x81c115c] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x81c115c] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x8333be4] main interface error: option qt-volume-complete does not exist
[0x8333be4]  skins2 interface error: no suitable dialogs provider found (hint:  compile the qt4 plugin, and make sure it is loaded properly)
[0x8333be4] skins2 interface error: cannot instanciate qt4 dialogs provider
[0x81c115c] main libvlc error: interface "default" initialization failed

and when i typed sudo find /usr -iname vlc,i got this output
developer@developer-desktop:~$ sudo find /usr -iname vlc
[sudo] password for developer: 
/usr/bin/vlc
/usr/lib/vlc
/usr/lib/mime/packages/vlc
/usr/share/vlc
/usr/share/doc/vlc
/usr/share/lintian/overrides/vlc
/usr/share/bug/vlc
/usr/share/menu/vlc
/usr/local/include/vlc
/usr/local/lib/vlc
/usr/local/share/vlc
/usr/local/share/doc/vlc

i'm new to ubuntu,please help

---

