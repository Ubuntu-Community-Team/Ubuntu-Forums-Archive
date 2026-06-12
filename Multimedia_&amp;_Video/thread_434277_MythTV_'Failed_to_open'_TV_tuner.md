---
title: "MythTV 'Failed to open' TV tuner"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by rickrude on 2007-05-05
Could someone please point me in the right direction?

I have mythTV backend and frontend on the same box, with a Twinhan 3020c tuner which is recognised by the kernel. 

I added modprobe dvb-bt8xx and modprobe dst to rc.local, after which I was able to add the card via mythtv-setup. 
However, when I try to channel scan, myth says 'Failed to open card'. When I run mythtv-setup from terminal, this is the output

I am not a Linux expert so can someone who is please decipher this?


```
$ mythtv-setup
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-05-06 09:47:16.662 Using runtime prefix = /usr
2007-05-06 09:47:16.673 Gnome-Screensaver support enabled
2007-05-06 09:47:16.674 DPMS is active.
2007-05-06 09:47:16.709 New DB connection, total: 1
2007-05-06 09:47:16.715 Connected to database 'mythconverg' at host: localhost
2007-05-06 09:47:16.718 Total desktop dim: 1280x720, with 1 screen[s].
2007-05-06 09:47:16.722 Using screen 0, 1280x720 at 0,0
2007-05-06 09:47:16.844 Current Schema Version: 1160
2007-05-06 09:47:16.864 Total desktop dim: 1280x720, with 1 screen[s].
2007-05-06 09:47:16.865 Using screen 0, 1280x720 at 0,0
2007-05-06 09:47:16.867 Switching to square mode (Titivillus)
2007-05-06 09:47:16.896 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-05-06 09:47:17.209 Joystick disabled.
2007-05-06 09:47:17.396 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-05-06 09:47:36.061 DiSEqCDevTree, Warning: No device tree for cardid 4
2007-05-06 09:47:36.082 DiSEqCDevTree, Warning: No device tree for cardid 4

```


Thanks.

---

### Post by striscio on 2007-05-28
I have the same problem with a Terratec HT PCI, recognized by the kernel after having recompiled the latest v4l drivers. Did you find some info?

---

### Post by Scyfer on 2007-08-20
I'm having the same problem does anyone have a fix.

---

### Post by coxy on 2007-08-30
The fix is on this post:

[http://ubuntuforums.org/showthread.php?p=1762954](http://ubuntuforums.org/showthread.php?p=1762954)

You need to comment out the wacom devices in your xorg.conf file. It worked for me.

---

