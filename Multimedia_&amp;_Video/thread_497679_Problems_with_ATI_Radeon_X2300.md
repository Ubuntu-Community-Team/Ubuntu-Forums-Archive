---
title: "Problems with ATI Radeon X2300"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by merlos on 2007-07-10
Hi all,
I'm trying to solve some issue with my Asus F3Jseries and my ATI Radeon X2300.

How you can see

```

merlos@merlos:~$ lspci -n | grep 0300
01:00.0 0300: 1002:718a
merlos@merlos:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 718a
```

my video card is an unknown device for my updated Feisty

```
merlos@merlos:~$ uname -a
Linux merlos 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

```

any hint to solve this issue?? 
do I need to upgrade my kernel or new derivers??

Tks in advance

Giovanni

---

### Post by ShagzModo on 2007-07-14
I have the exact same problem with a Asus A8JR notebook.
the driver i can install supports upto x1800 videocard.
If anyone knows where to obtain the latest linux driver i be very happy

---

### Post by Furax- on 2007-07-16
Same problem here, on my Asus F5V series.. Let me know if there's any news

---

### Post by ckh on 2007-07-21
I had excact the same problem when I just changed my laptop to HP 6910p
but I just solved this probelem.

steps below:

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo /etc/init.d/gdm restart

(This solution was form [http://terenzioberni.blogspot.com/2007/06/ubuntu-704-on-asus-z53jr-f3jr.html](http://terenzioberni.blogspot.com/2007/06/ubuntu-704-on-asus-z53jr-f3jr.html))


-ckh

---

### Post by dgrafix on 2007-10-09
I followed this and it at least got my X server working so thanks :)

However, Im still having problems getting 3D to work. its a  ATI Radeon Mobility X2300

I noticed im getting ATI Technologies Inc Unknown device 7210 when i poll the pci devices :/

Here is a dump of all my relevent stuff:

```
dan@danslaptop:~$ glxinfo |grep direct
libGL error: failed to open DRM: Operation not permitted
libGL error: reverting to (slow) indirect rendering
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect


dan@danslaptop:~$ fglrxinfo
libGL error: failed to open DRM: Operation not permitted
libGL error: reverting to (slow) indirect rendering
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)


dan@danslaptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7210 (rev ce)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
dan@danslaptop:~$ 

```

Xorg (relevent bits):
```

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
      #  Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "Monitor"
#	VertRefresh  43.0 - 60.0
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
#	HorizSync    28.0 - 51.0
	Option	    "DPMS" "true"
EndSection

Section "Device"
#	BusID       "PCI:1:0:0"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option 	"RenderAccel" "True"	
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
        Option      "Composite" "disable"
EndSection

```

---

### Post by blackmx on 2007-11-24
i have the same problem =\
Desktop effects don't work

---

### Post by Yellow Pasque on 2007-11-25
Also try:
> sudo update-pciids

---

### Post by Peter Great on 2008-04-23
I also have the same problem with ATI Mobility Radeon X2300. 3D direct rendering does not work.
I searched online, and it seems that while many ATI graphics cards work fine under Linux, no one has had any success with the specific model 'ATI Mobility Radeon X2300' (I mean getting 3D acceleration to work).
If anyone has actually done so, please tell me and I'll very much appreciate your help!

---

### Post by dgrafix on 2008-04-25
I think its just a way too old DX only pain in the bum. I couldnt get OpenGL working under windows either, only directX7 which also ran crap.

---

