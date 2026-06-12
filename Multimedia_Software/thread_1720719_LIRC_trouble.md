---
title: "LIRC trouble"
date: 2011-04-03
forum: Multimedia Software
---

### Post by bruderbell on 2011-04-03
Hi folks,
I think I originally posted this in the wrong section.

I'll try to give relevant details. I'm no expert at any of this, so please tell me what I've done wrong.

I ordered up a MCE Remote, USB interface, for my linux box. Today I plugged it in and promptly googled for instructions and ideas on getting it working. I installed LIRC, seemingly without incident. When I run IRW, I can tell that a few buttons have effect (volume, mute, one button seems to press the ALT key, I have a right and left click button, etc). However, I can't figure out how to get the remote working in MythTV. Outside of MythTV, the arrow keys on the remote move my mouse around. Inside MythTV, the remote does nothing.

Potentially useful stuff:
bruderbell@mythtv:~/Desktop/temp$ dmesg | grep lirc
[ 23.258753] lirc_dev: IR Remote Control driver registered, major 61 
[ 23.268274] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[ 23.268277] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[ 23.268300] usbcore: registered new interface driver lirc_mceusb
bruderbell@mythtv:~/Desktop/temp$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 005 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0755:2626 Aureal Semiconductor 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bruderbell@mythtv:~/Desktop/temp$ irrecord test

irrecord - application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not get file information for /dev/lirc
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

Any ideas out there?

Thanks

---

