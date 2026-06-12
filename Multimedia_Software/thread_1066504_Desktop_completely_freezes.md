---
title: "Desktop completely freezes"
date: 2009-02-10
forum: Multimedia Software
---

### Post by tehk on 2009-02-10
Just going about my daily things, with firefox and dolphin open when my desktop becomes completely frozen. I am still able to ssh into the machine from another box and I tried to restart kdm to see if I could restore things, and this is what I got:

/etc/init.d/kdm restart
Stopping K Display Manager: kdm not responding to TERM signal (pid 6399).
Starting K Display Manager: kdm.

When I do a top, I can see Xorg is consuming 100% cpu and I cannot kill that process either.

I suspect its a faulty video card driver, but could be wrong.

Below is my xorg.conf:

```
# cat /etc/X11/xorg.conf
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "EnableMonitor" "crt1,lvds,tv,tmds1,crt2,tmds2,cv,tmds2i"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Any ideas?

---

### Post by polobreaka on 2009-02-11
i am experiencing the same issue. while using the computer, doesnt matter what program, or how long ive been using it. it would randomly hangs for a couple of minutes, then it will eventually come back. im pretty frustrated with this issue. i cant figure out what it could be. possibly video card driver? im running nvidia geforce 9500 gt 512 ddr2 and i installed the 180.22 driver. im not sure if i am actually running 180.22 or 180.11. how can i find out? when the freeze is over, i try to look at the system log to see if anything displays, cant really tell. is there any way i can look for any errors that mightve logged elsewhere? thanks. 

im dual booting with vista and im actually liking ubuntu 8.10 alot, but this random freezing is making me want to quit.

---

### Post by tehk on 2009-02-11
you should be able to tell what version your driver is by opening the nvidia-settings app from the control menu, i know where it is kubuntu only.

i myself use an ati 3200 with the only drivers available, lol, we get **** support from ati....

also in my situation, the computer doesnt come back, it stays frozen forever. I cant even control-alt-F5 to get to another tty.... so im not sure if its video driver related or something else.

---

