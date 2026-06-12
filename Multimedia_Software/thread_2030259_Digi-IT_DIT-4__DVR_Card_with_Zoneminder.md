---
title: "Digi-IT DIT-4  DVR Card with Zoneminder"
date: 2012-07-20
forum: Multimedia Software
---

### Post by liverpoolatnight on 2012-07-20
Has anyone got a good bttv.conf for this working under zoneminder?

Here are some info from [http://www.irc.com.my/ircsystem/digiit/4ch.php](http://www.irc.com.my/ircsystem/digiit/4ch.php)

Frame Rate for Monitoring: 30 fps (NTSC) / 25 fps (PAL)

Image Size (resolution)
NTSC 320x240, 640x240, 640x480
PAL 352x288, 704x288, 704x576

Remote Control: Setting, Display Control, Relay Output, PTZ Camera - PTZ is what im hoping to get going but im 100% is a serial port you attach on the DVR card
Relay Output - Don't attend to us it

1 input audio record channel (I have no need to record so i dunno)

Watchdog (I have no idea what is it)

Operating System Windows 2000, XP, 2003 (Tryed it on XP and windows 2003 with i-Catcher Console using [http://www.icode.co.uk/icatcher/products/console.html](http://www.icode.co.uk/icatcher/products/console.html)

My cards info
francis@DELLGX520 ~ $ sudo lsmod |grep videodev
[sudo] password for francis: 
videodev               85626  5 tuner,tvaudio,tda7432,bttv,v4l2_common

sudo lspci | grep Bt878
04:02.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
04:02.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)[/quote]


04:02.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
	Subsystem: Device 300a:dd11
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at f0001000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: bttv
	Kernel modules: bttv

04:02.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
	Subsystem: Device 300a:dd11
	Flags: bus master, medium devsel, latency 64, IRQ 3
	Memory at f0000000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied>

sudo lsmod |grep videodev
videodev  85626  5 tuner,tvaudio,tda7432,bttv,v4l2_common

---

