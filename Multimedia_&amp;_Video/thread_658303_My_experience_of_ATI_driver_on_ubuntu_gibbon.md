---
title: "My experience of ATI driver on ubuntu gibbon"
date: 2008-01-04
forum: Multimedia &amp; Video
---

### Post by hx129 on 2008-01-04
I have a dell vostro 1000 laptop with AMD 64x2 cpu and ATI Express 1150 display adaptor. The ATI driver I use is 8.443 from ati's website. I use Ubuntu 7.10.

(1) I first build the package from The 8.443 driver from ATI using "ati....run --buildpkg Ubuntu/gutsy"

(2) Since I use Xgl previously, I have to remove xorg-driver-fglrx and xserver-xgl first, Then I install the above ati packages(there are 4 of them). The package compiles and installs the kernel module automatically now.

(3) close X, do "depmod -a" and be sure to "rmmod fglrx".(although you uninstall the old fglrx in the harddriver, it is still in the memory!!!)

(4) add fglrx to the whitelist in /usr/bin/compiz (which is a bash script)

(5) Enable AIGLX and composite extension in /etc/X11/xorg.conf

Option		"AIGLX"	"true"

Option		"Composite"	"true"

Here is my device section

Section "Device"
	Identifier	"ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Busid		"PCI:1:5:0"
EndSection

(7) restart X, enable the visual effects in system\preference menu.

If it doesn't work, a helpful debugging method is try to invoke compiz in a terminal first: run "compiz --replace", and see what happened.

In my case, I need to modify the beginning of /usr/bin/compiz. Change the path at the beginning from "/usr/local/bin" to "/usr/bin".


Problems:

mplayer plays movie properly only under full screen mode. sound is ok. but there's no video under non-full screen mode. 

There're some cryptic message in dmesg, which I don't think is related to the problem above: 

[  907.108000] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list

Also, the compiz reports the dbus plugin doesn't work.

---

