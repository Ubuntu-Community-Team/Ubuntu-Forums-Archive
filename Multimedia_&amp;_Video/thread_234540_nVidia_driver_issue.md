---
title: "nVidia driver issue"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by PendragonUK on 2006-08-11
OK I have read loads, followed Howto's all with no luck...
This is whats happening. I follow the howto, step by step. On reboot the cooling fan on the G/Card slows (good point) I hear the double drum for logon but there is no output from the monitor.

So I recone that the driver install fine, well it knows how to control the speed of the fan. ubuntu is happy because it wants me to logon. Either the card isn't sending any signel or more likly the monitor can't handle what is being sent.

I'm going to try to edit the xorg.conf with the corect monitor settings before restart... Fingers crossed](*,) ](*,) 

AMD 64 Sempron 3400
2.6.15-26-amd64-generic
PCI-E nVidia 7900 256Mb GT 
LCD 17'' flatpanel

---

### Post by mlind on 2006-08-11
Try to auto-generate xorg.conf
```

sudo dpkg-reconfigure xserver-xorg

```

If you're using propietary nvidia drivers, choose **nvidia** as gfx driver.

---

### Post by inkapyrite on 2006-08-11
it could be because your LCD couldn't handle the refresh rate your gcard was churning out with the nvidia drivers. I had this problem too where i heard the drums but the monitor remained blank. You can force your gcard to lower your res by editing xorg.conf. check out my previous post on this:

[http://www.ubuntuforums.org/showthread.php?t=221313&page=2](http://www.ubuntuforums.org/showthread.php?t=221313&page=2)

---

### Post by tseliot on 2006-08-12
If what they suggested didn't solve the problem you can try point 4 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

---

### Post by PendragonUK on 2006-08-12
thanks for the suggestions... No luck so far. I'm getting used to editing xorg.conf with nano ;) 

So far I have tryed...

Droping out of xserver and useing 

```
sudo dpkg-reconfigure xserver-xorg
```

To switch to the installed nvidia drivers and specifiy the correct monitor setings.

Also using nano edit the xorg.conf file to check out that the correct Horizontal and Vertical frequencey is used for the monitor.

Still no change in the result, black screen with the monitor complaining of "No Signel" at login, but with sounds of a normal system start.

I know that is is a lot to ask but could someone please do some handholding and baby-step me through this?

I'll try to provide as much info as I can... (With links to spec sheets if possible)

G/Card
BFG Tech PCI-E nVidia 7900 256 GT-OC 
[http://www.bfgtech.com/images/BFG%20spec%20sheet%20pdfs/7900GT_256MB_PCIE_sheet.pdf](http://www.bfgtech.com/images/BFG%20spec%20sheet%20pdfs/7900GT_256MB_PCIE_sheet.pdf)

Monitor
iMax LM-17N
[http://www.akcom.net/index3.php?prodid=4144&catcode=6&subcatcode=28](http://www.akcom.net/index3.php?prodid=4144&catcode=6&subcatcode=28)

Motherboard
ASUS K8N4-E SE
[http://www.asus.com/products4.aspx?modelmenu=2&model=980&l1=3&l2=14&l3=0](http://www.asus.com/products4.aspx?modelmenu=2&model=980&l1=3&l2=14&l3=0)

CPU
AMD Sempron64 3400

uname -r = 
2.6.15-26-amd64-generic

ubuntu 64 clean install + automatic updates

nVidia drivers installed using...

```
sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r`

```

PS sorry about the poor spelling I haven't gotten spell-checker figured 8-[

---

### Post by tseliot on 2006-08-12
1) Post the output of this command:
```
lspci -n | grep 0300
```

2) let's try to diagnose the error:

Boot with the "nv" driver in your xorg.conf

Then (after Ubuntu has booted) Set the driver to "nvidia" in your /etc/X11/xorg.conf
Log out and Press CTRL+ALT+F1

You will get to the command line (no GUI)
Type:

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then:
```
startx -- -verbose 5 -logverbose 5
```

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C (select NO if it asks you if you want to see the output of the error or something like that)

Then type this in order to copy the output of the error to your home folder:
```
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
```
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "nv" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

Then
```
sudo /etc/init.d/gdm restart (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm restart (if you use KDM)
```


Post the content of that file (which you can find under /home/your_username/Xorg.0.log )

---

### Post by VirtuAlex on 2006-08-12
I know it is highly unlikely would help, but here is the story. I know one lady who has brand new flat screen monitor and windows xp. Every time she boots the computer she has to turn the power off the monitor and turn it on again. Otherwise there is no picture. I do not remember if she has power button on the monitor, but if she does, it does not do any good. She actually has to unplug the power cord from the outlet. For that matter she arranged separate extension cord with power switch just for that damn monitor. I suggested her calling manufacturer (I do not remember the make though) but she told me she got used to it. She just never turns the computer off. Itn't that amazing?

---

### Post by PendragonUK on 2006-08-12
tseliot in answer to your first point...

> 1) Post the output of this command:

```

lspci -n | grep 0300
```




0000:01:00.0 0300: 10de:0291 (rev a1)


This is when running on the nv drivers

I'm just about to try point 2, I will get back to you with the results...

---

### Post by tseliot on 2006-08-12
I've noticed that I didn't ask you 2 things which are crucial for me to know:

1) which guide did you follow to install the driver?

2) did you install the driver from the repositories of from Nvidia's website?

---

### Post by PendragonUK on 2006-08-12
The giuld I followed was yours ;) I tryed method one and then method two. There have been several clean reinstalls in this prosess ](*,) I have learnt to edit the xorg.conf to save me having to clean install ubuntu each time I screw up :o 

The current driver install method is yours from the Howto method three.

```
sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r`
```

So back to my attempts to follow simple instructions...

Boot under nv drivers, edit xorg.conf and switch to the nvidia driver. I log out and press CTRL+ALT+F1  Nothing... nothing hapens! I'm sat there looking at the log in screen:mad:  OK I restart the PC, choose the second boot option, "recovery" from there I can continue to follow your instructions.

the output from the verbose log for startx... will follow in the next post, too long apparently:roll: 




Now the thing is, I have been messing with this for quite some time... All sorts of errors could have crept in due to my incompitance. I'm more than willing to go back to square one and clean install this pig if that is what you recomend. 

Thanks for your time :D

---

### Post by PendragonUK on 2006-08-12
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 x86_64
Current Operating System: Linux pendragon-desktop 2.6.15-26-amd64-generic #1 SMP PREEMPT Thu Aug 3 02:52:35 UTC 2006 x86_64
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug 12 18:11:47 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "flat Panel 17''"
(**) |   |-->Device "NVIDIA Corporation NVIDIA GeForce 7900GT"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(--) using VT number 2

---

### Post by PendragonUK on 2006-08-12
(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,005e card 1043,815a rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 1043,815a rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 1043,815a rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 1043,815a rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 1043,815a rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:06:0: chip 10de,0053 card 1043,815a rev f2 class 01,01,8a hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0291 card 19f1,20a1 rev a1 class 03,00,00 hdr 00
(II) PCI: 05:07:0: chip 1102,0007 card 1102,100a rev 00 class 04,01,00 hdr 00
(II) PCI: 05:08:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:9:0), (0,5,5), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xd3000000 - 0xd30fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:11:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:13:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:14:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd2ffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x0291) rev 161, Mem @ 0xd0000000/24, 0xc0000000/28, 0xd1000000/24, I/O @ 0xc000/7, BIOS @ 0xd2000000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xd3000000 - 0xd30000ff (0x100) MX[B]
	[1] -1	0	0xd3101000 - 0xd31010ff (0x100) MX[B]
	[2] -1	0	0xd3100000 - 0xd3100fff (0x1000) MX[B]
	[3] -1	0	0xd2000000 - 0xd201ffff (0x20000) MX[B](B)
	[4] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[5] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[8] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[9] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[10] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[11] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[12] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[13] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd3000000 - 0xd30000ff (0x100) MX[B]
	[1] -1	0	0xd3101000 - 0xd31010ff (0x100) MX[B]
	[2] -1	0	0xd3100000 - 0xd3100fff (0x1000) MX[B]
	[3] -1	0	0xd2000000 - 0xd201ffff (0x20000) MX[B](B)
	[4] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[5] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[8] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[9] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[10] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[11] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[12] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[13] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd3000000 - 0xd30000ff (0x100) MX[B]
	[5] -1	0	0xd3101000 - 0xd31010ff (0x100) MX[B]
	[6] -1	0	0xd3100000 - 0xd3100fff (0x1000) MX[B]
	[7] -1	0	0xd2000000 - 0xd201ffff (0x20000) MX[B](B)
	[8] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[14] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[15] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[16] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[17] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[19] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B](B)

---

### Post by tseliot on 2006-08-12
> **PendragonUK said:**
> The giuld I followed was yours ;) I tryed method one and then method two. There have been several clean reinstalls in this prosess ](*,) I have learnt to edit the xorg.conf to save me having to clean install ubuntu each time I screw up :o 

The current driver install method is yours from the Howto method three.

```
sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r`
```

So back to my attempts to follow simple instructions...

Boot under nv drivers, edit xorg.conf and switch to the nvidia driver. I log out and press CTRL+ALT+F1  Nothing... nothing hapens! I'm sat there looking at the log in screen:mad:  OK I restart the PC, choose the second boot option, "recovery" from there I can continue to follow your instructions.

the output from the verbose log for startx... will follow in the next post, too long apparently:roll: 




Now the thing is, I have been messing with this for quite some time... All sorts of errors could have crept in due to my incompitance. I'm more than willing to go back to square one and clean install this pig if that is what you recomend. 

Thanks for your time :D
Try my Envy script which (usually) solves conflicts and then report to me.

[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

---

### Post by PendragonUK on 2006-08-12
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA X Driver  1.0-8762  Mon May 15 14:01:11 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Found 1 NVIDIA X Screens
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd3000000 - 0xd30000ff (0x100) MX[B]
	[5] -1	0	0xd3101000 - 0xd31010ff (0x100) MX[B]
	[6] -1	0	0xd3100000 - 0xd3100fff (0x1000) MX[B]
	[7] -1	0	0xd2000000 - 0xd201ffff (0x20000) MX[B](B)
	[8] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[14] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[15] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[16] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[17] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[19] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B](B)

---

### Post by PendragonUK on 2006-08-12
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd3000000 - 0xd30000ff (0x100) MX[B]
	[5] -1	0	0xd3101000 - 0xd31010ff (0x100) MX[B]
	[6] -1	0	0xd3100000 - 0xd3100fff (0x1000) MX[B]
	[7] -1	0	0xd2000000 - 0xd201ffff (0x20000) MX[B](B)
	[8] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[18] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[19] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[20] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[22] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B](B)
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(==) NVIDIA(0): Using HW cursor
(**) NVIDIA(0): Enabling RENDER acceleration
(==) NVIDIA(0): Video key set to default value of 0x101fe
(II) NVIDIA(0): NVIDIA GPU GeForce 7900 GT at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(II) NVIDIA(0): GPU Architecture: 0x40
(II) NVIDIA(0): GPU Implementation: 0x49
(II) NVIDIA(0): GPU Revision: 0xa2
(--) NVIDIA(0): VideoBIOS: 05.71.22.14.02
(--) NVIDIA(0): Found 2 CRTCs on board
(II) NVIDIA(0): Supported display device(s): CRT-0, CRT-1, DFP-0, DFP-1, TV-0
(II) NVIDIA(0): Bus detected as PCI Express
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): VPES : 8
(II) NVIDIA(0): SPS  : 24
(II) NVIDIA(0): 
(II) NVIDIA(0): Mode timing constraints for  : GeForce 7900 GT
(II) NVIDIA(0): Maximum mode timing values   :
(II) NVIDIA(0):     Horizontal Visible Width : 8192
(II) NVIDIA(0):     Horizontal Blank Start   : 8192
(II) NVIDIA(0):     Horizontal Blank Width   : 4096
(II) NVIDIA(0):     Horizontal Sync Start    : 8184
(II) NVIDIA(0):     Horizontal Sync Width    : 504
(II) NVIDIA(0):     Horizontal Total Width   : 8224
(II) NVIDIA(0):     Vertical Visible Height  : 8192
(II) NVIDIA(0):     Vertical Blank Start     : 8192
(II) NVIDIA(0):     Vertical Blank Width     : 256
(II) NVIDIA(0):     Veritcal Sync Start      : 8191
(II) NVIDIA(0):     Vertical Sync Width      : 15
(II) NVIDIA(0):     Vertical Total Height    : 8193
(II) NVIDIA(0): 
(II) NVIDIA(0): Minimum mode timing values   :
(II) NVIDIA(0):     Horizontal Total Width   : 40
(II) NVIDIA(0):     Vertical Total Height    : 2
(II) NVIDIA(0): 
(II) NVIDIA(0): Mode timing alignment        :
(II) NVIDIA(0):     Horizontal Visible Width : multiples of 8
(II) NVIDIA(0):     Horizontal Blank Start   : multiples of 8
(II) NVIDIA(0):     Horizontal Blank Width   : multiples of 8
(II) NVIDIA(0):     Horizontal Sync Start    : multiples of 8
(II) NVIDIA(0):     Horizontal Sync Width    : multiples of 8
(II) NVIDIA(0):     Horizontal Total Width   : multiples of 8
(II) NVIDIA(0): 
(--) NVIDIA(0): Connected display device(s) on GeForce 7900 GT at PCI:1:0:0:
(--) NVIDIA(0):     RTK 17'' LCDMonitor (CRT-1)
(--) NVIDIA(0): RTK 17'' LCDMonitor (CRT-1): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): 
(--) NVIDIA(0): --- EDID for RTK 17'' LCDMonitor (CRT-1) ---
(--) NVIDIA(0): EDID Version                 : 1.1
(--) NVIDIA(0): Manufacturer                 : RTK
(--) NVIDIA(0): Monitor Name                 : RTK 17'' LCDMonitor
(--) NVIDIA(0): Product ID                   : 0
(--) NVIDIA(0): 32-bit Serial Number         : 16843009
(--) NVIDIA(0): Serial Number String         : 000001
(--) NVIDIA(0): Manufacture Date             : 2002, week 30
(--) NVIDIA(0): DPMS Capabilities            : Standby Suspend Active Off
(--) NVIDIA(0): Prefer first detailed timing : No
(--) NVIDIA(0): Supports GTF                 : No
(--) NVIDIA(0): Maximum Image Size           : 360mm x 270mm
(--) NVIDIA(0): Valid HSync Range            : 20 kHz - 92 kHz
(--) NVIDIA(0): Valid VRefresh Range         : 43 Hz - 85 Hz
(--) NVIDIA(0): EDID maximum pixel clock     : 157.5 MHz
(--) NVIDIA(0): 
(--) NVIDIA(0): Established Timings:
(--) NVIDIA(0):   640  x 480  @ 60 Hz
(--) NVIDIA(0):   640  x 480  @ 72 Hz
(--) NVIDIA(0):   640  x 480  @ 75 Hz
(--) NVIDIA(0):   800  x 600  @ 56 Hz
(--) NVIDIA(0):   800  x 600  @ 60 Hz
(--) NVIDIA(0):   800  x 600  @ 72 Hz
(--) NVIDIA(0):   800  x 600  @ 75 Hz
(--) NVIDIA(0):   1024 x 768  @ 70 Hz
(--) NVIDIA(0):   1280 x 1024 @ 75 Hz
(--) NVIDIA(0): 
(--) NVIDIA(0): Standard Timings:
(--) NVIDIA(0):   1024 x 768  @ 60 Hz
(--) NVIDIA(0):   1024 x 768  @ 75 Hz
(--) NVIDIA(0):   1024 x 768  @ 85 Hz
(--) NVIDIA(0):   1152 x 864  @ 75 Hz
(--) NVIDIA(0):   1280 x 960  @ 60 Hz
(--) NVIDIA(0):   1280 x 960  @ 85 Hz
(--) NVIDIA(0):   1280 x 1024 @ 85 Hz
(--) NVIDIA(0): 
(--) NVIDIA(0): --- End of EDID for RTK 17'' LCDMonitor (CRT-1) ---

---

### Post by PendragonUK on 2006-08-12
(--) NVIDIA(0): 
(II) NVIDIA(0): Frequency information for RTK 17'' LCDMonitor (CRT-1):
(II) NVIDIA(0):   HorizSync   : 20.000-92.000 kHz
(II) NVIDIA(0):   VertRefresh : 43.000-85.000 Hz
(II) NVIDIA(0):     (HorizSync from EDID)
(II) NVIDIA(0):     (VertRefresh from EDID)
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Modes in ModePool for RTK 17'' LCDMonitor (CRT-1) ---
(II) NVIDIA(0): "nvidia-auto-select"   : 1024 x  768 @  85.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1680x1050"            : 1680 x 1050 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1680x1050_60"         : 1680 x 1050 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1680x1050_60_0"       : 1680 x 1050 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1600x1024"            : 1600 x 1024 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1600x1024_60"         : 1600 x 1024 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1440x900"             : 1440 x  900 @  60.2 Hz  (from: X Server)
(II) NVIDIA(0): "1440x900_60"          : 1440 x  900 @  60.2 Hz  (from: X Server)
(II) NVIDIA(0): "1400x1050"            : 1400 x 1050 @  74.8 Hz  (from: X Server)
(II) NVIDIA(0): "1400x1050_75"         : 1400 x 1050 @  74.8 Hz  (from: X Server)
(II) NVIDIA(0): "1400x1050_70"         : 1400 x 1050 @  70.0 Hz  (from: X Server)
(II) NVIDIA(0): "1400x1050_60"         : 1400 x 1050 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1280x1024"            : 1280 x 1024 @  85.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1280x1024_85"         : 1280 x 1024 @  85.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1280x1024_75"         : 1280 x 1024 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1280x1024_60"         : 1280 x 1024 @  60.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1280x960"             : 1280 x  960 @  85.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1280x960_85"          : 1280 x  960 @  85.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1280x960_60"          : 1280 x  960 @  60.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1280x800"             : 1280 x  800 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1280x800_60"          : 1280 x  800 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1280x768"             : 1280 x  768 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1280x768_60"          : 1280 x  768 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1152x864"             : 1152 x  864 @  85.1 Hz  (from: X Server)
(II) NVIDIA(0): "1152x864_85"          : 1152 x  864 @  85.1 Hz  (from: X Server)
(II) NVIDIA(0): "1152x864_75"          : 1152 x  864 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1152x768"             : 1152 x  768 @  54.8 Hz  (from: X Server)
(II) NVIDIA(0): "1152x768_55"          : 1152 x  768 @  54.8 Hz  (from: X Server)
(II) NVIDIA(0): "1024x768"             : 1024 x  768 @  85.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1024x768_85"          : 1024 x  768 @  85.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1024x768_75_0"        : 1024 x  768 @  75.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1024x768_75"          : 1024 x  768 @  75.0 Hz  (from: EDID)
(II) NVIDIA(0): "1024x768_70"          : 1024 x  768 @  70.1 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1024x768_60"          : 1024 x  768 @  60.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "960x720"              :  960 x  720 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "960x720d60"           :  960 x  720 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "960x600"              :  960 x  600 @  72.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "960x600d73"           :  960 x  600 @  72.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "960x600d60"           :  960 x  600 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "928x696"              :  928 x  696 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "928x696d60"           :  928 x  696 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "896x672"              :  896 x  672 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "896x672d60"           :  896 x  672 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "840x525"              :  840 x  525 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "840x525d60"           :  840 x  525 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "840x525d60_0"         :  840 x  525 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "832x624"              :  832 x  624 @  74.5 Hz  (from: X Server)
(II) NVIDIA(0): "832x624_75"           :  832 x  624 @  74.5 Hz  (from: X Server)
(II) NVIDIA(0): "800x600"              :  800 x  600 @  85.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "800x600_85"           :  800 x  600 @  85.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "800x600_75"           :  800 x  600 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "800x600_72"           :  800 x  600 @  72.2 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "800x600d70"           :  800 x  600 @  70.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "800x600d65"           :  800 x  600 @  65.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "800x600_60"           :  800 x  600 @  60.3 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "800x600d60"           :  800 x  600 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "800x600_56"           :  800 x  600 @  56.2 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "800x512"              :  800 x  512 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "800x512d60"           :  800 x  512 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "720x450"              :  720 x  450 @  60.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "720x450d60"           :  720 x  450 @  60.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "720x400"              :  720 x  400 @  85.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "720x400_85"           :  720 x  400 @  85.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "700x525"              :  700 x  525 @  74.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "700x525d75"           :  700 x  525 @  74.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "700x525d70"           :  700 x  525 @  70.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "700x525d60"           :  700 x  525 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x512"              :  640 x  512 @  85.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x512d85"           :  640 x  512 @  85.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x512d75"           :  640 x  512 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x512d60"           :  640 x  512 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480"              :  640 x  480 @  85.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480d85"           :  640 x  480 @  85.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480_85"           :  640 x  480 @  85.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480_75"           :  640 x  480 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "640x480_73"           :  640 x  480 @  72.8 Hz  (from: EDID)
(II) NVIDIA(0): "640x480_73_0"         :  640 x  480 @  72.8 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480d60"           :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480_60_0"         :  640 x  480 @  60.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480_60"           :  640 x  480 @  60.0 Hz  (from: EDID)
(II) NVIDIA(0): "640x400"              :  640 x  400 @  85.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x400_85"           :  640 x  400 @  85.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x400d60"           :  640 x  400 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x384"              :  640 x  384 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x384d60"           :  640 x  384 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x350"              :  640 x  350 @  85.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x350_85"           :  640 x  350 @  85.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "576x432"              :  576 x  432 @  85.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d85"           :  576 x  432 @  85.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d75"           :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x384"              :  576 x  384 @  54.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x384d55"           :  576 x  384 @  54.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384"              :  512 x  384 @  85.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d85"           :  512 x  384 @  85.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d75"           :  512 x  384 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d70"           :  512 x  384 @  70.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d60"           :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "416x312"              :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "416x312d75"           :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300"              :  400 x  300 @  85.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d85"           :  400 x  300 @  85.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d75"           :  400 x  300 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d72"           :  400 x  300 @  72.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d60"           :  400 x  300 @  60.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d56"           :  400 x  300 @  56.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "360x200"              :  360 x  200 @  85.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "360x200d85"           :  360 x  200 @  85.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240"              :  320 x  240 @  85.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d85"           :  320 x  240 @  85.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d75"           :  320 x  240 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d73"           :  320 x  240 @  72.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d60"           :  320 x  240 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x200"              :  320 x  200 @  85.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x200d85"           :  320 x  200 @  85.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x175"              :  320 x  175 @  85.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x175d85"           :  320 x  175 @  85.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): --- End of ModePool for RTK 17'' LCDMonitor (CRT-1): ---

---

### Post by PendragonUK on 2006-08-12
(II) NVIDIA(0): 
(II) NVIDIA(0): Assigned Display Device: CRT-1
(II) NVIDIA(0): Requested modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0): MetaMode "1280x1024":
(II) NVIDIA(0):     Bounding Box: [0, 0, 1280, 1024]
(II) NVIDIA(0):     RTK 17'' LCDMonitor (CRT-1): "1280x1024"
(II) NVIDIA(0):         Size          : 1280 x 1024
(II) NVIDIA(0):         Offset        : +0 +0
(II) NVIDIA(0):         Panning Domain: @ 1280 x 1024
(II) NVIDIA(0):         Position      : [0, 0, 1280, 1024]
(II) NVIDIA(0): MetaMode "1024x768":
(II) NVIDIA(0):     Bounding Box: [0, 0, 1024, 768]
(II) NVIDIA(0):     RTK 17'' LCDMonitor (CRT-1): "1024x768"
(II) NVIDIA(0):         Size          : 1024 x 768
(II) NVIDIA(0):         Offset        : +0 +0
(II) NVIDIA(0):         Panning Domain: @ 1024 x 768
(II) NVIDIA(0):         Position      : [0, 0, 1024, 768]
(II) NVIDIA(0): MetaMode "800x600":
(II) NVIDIA(0):     Bounding Box: [0, 0, 800, 600]
(II) NVIDIA(0):     RTK 17'' LCDMonitor (CRT-1): "800x600"
(II) NVIDIA(0):         Size          : 800 x 600
(II) NVIDIA(0):         Offset        : +0 +0
(II) NVIDIA(0):         Panning Domain: @ 800 x 600
(II) NVIDIA(0):         Position      : [0, 0, 800, 600]
(II) NVIDIA(0): MetaMode "640x480":
(II) NVIDIA(0):     Bounding Box: [0, 0, 640, 480]
(II) NVIDIA(0):     RTK 17'' LCDMonitor (CRT-1): "640x480"
(II) NVIDIA(0):         Size          : 640 x 480
(II) NVIDIA(0):         Offset        : +0 +0
(II) NVIDIA(0):         Panning Domain: @ 640 x 480
(II) NVIDIA(0):         Position      : [0, 0, 640, 480]
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(WW) NVIDIA(0): No size information available in CRT-1's EDID; cannot compute
(WW) NVIDIA(0):     DPI from EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] 0	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xd3000000 - 0xd30000ff (0x100) MX[B]
	[8] -1	0	0xd3101000 - 0xd31010ff (0x100) MX[B]
	[9] -1	0	0xd3100000 - 0xd3100fff (0x1000) MX[B]
	[10] -1	0	0xd2000000 - 0xd201ffff (0x20000) MX[B](B)
	[11] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[17] 0	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[22] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[23] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[24] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[26] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B](B)
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): kernel module enabled successfully
(II) NVIDIA(0): Memory mapped
(II) NVIDIA(0): Interrupts enabled
(II) NVIDIA(0): Setting mode "1280x1024"
(II) NVIDIA(0): CRT-1 assigned CRTC 0
(II) NVIDIA(0): First mode initialized
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Visuals set up
(II) NVIDIA(0): Pixmap depths set up
(II) NVIDIA(0): GLX visuals set up
(II) NVIDIA(0): Framebuffer set up
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): Default colormap initialized.
(II) NVIDIA(0): Palette loaded
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) NVIDIA(0): Screen initialization complete
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "uk"
(**) Generic Keyboard: XkbLayout: "uk"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/input/mice"
(II) Configured Mouse: ps2EnableDataReporting: succeeded

---

### Post by PendragonUK on 2006-08-12
Damn that was long... One way of getting my post count up I supose:twisted:

---

### Post by tseliot on 2006-08-12
> **tseliot said:**
> Try my Envy script which (usually) solves conflicts and then report to me.

[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

This is what I suggested before


> **PendragonUK said:**
> Damn that was long... One way of getting my post count up I supose:twisted:

I have also noticed this:
```
Found 2 CRTCs on board
```

Do you use 2 monitors? If so, please use only one of them.

---

### Post by PendragonUK on 2006-08-12
First off I only have one monitor... I did suggest that things may have become messed up...

Also I have followed your instructions for envy, after ./ it dumps me at the log on (No xserver) just plain command line. Then nothing... Just sits there.

Would it be a good idea to clean install ubuntu, then use envy? Hey I'm a windows user I'm used to haveing to clean install :p 

Or... make a new xorg.conf with 

```
sudo dpkg-reconfigur xserver-xorg
```

Then remove the current driver

```
sudo apt-get --purge remove nvidia-glx linux-restricted-modules-`uname -r`
```

Then try envy???

I'm more than happy to try just about anything you suggest...:D 

PS used envy_8762_64 Fingers crossed and everything.

---

### Post by PendragonUK on 2006-08-12
I have just re-read the instructions for envy... Dho I'm a fool! ](*,)  I report back in a few mins with the results...

---

### Post by PendragonUK on 2006-08-12
OK this time I followed the instructions for envy properly...

result for envy_8762_64...

No change, I hear the Tomtom drums but there is still no out put on the monitor...


I'm off for a bit my head hurts... going to watch some TV back later...

Thanks...

---

### Post by tseliot on 2006-08-12
please post the content of your xorg.conf

---

### Post by PendragonUK on 2006-08-12
The only change I have made is to change nvidia to nv. this was done by manualy editing the line in nano 

What I would like is to have the monitor running at 1280 x 1025 75Hz OK I know thats windows speak but if that is possible, that's what I would like...

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Mon May 15 14:17:32 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "uk"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "flat Panel 17''"
    HorizSync       31.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA GeForce 7900GT"
    Driver         "nv"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA GeForce 7900GT"
    Monitor        "flat Panel 17''"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

---

### Post by tseliot on 2006-08-13
> **PendragonUK said:**
> The only change I have made is to change nvidia to nv. this was done by manualy editing the line in nano 

What I would like is to have the monitor running at 1280 x 1025 75Hz OK I know thats windows speak but if that is possible, that's what I would like...

Try point 10 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then put "nvidia" instead of "nv" in your xorg.conf

Log out and press CTRL+ALT+Backspace. Then log in

---

### Post by PendragonUK on 2006-08-13
Off to try it, I'll report back with the results...

thanks for the support :)

---

### Post by PendragonUK on 2006-08-13
[size="6"]
Thank You[/size]

It is now working :-D 

Serousely though your help has taught me so much, I have been playing around with Linux on and off for years. I have tryed so mainy distros over that time. What drew me to ubuntu was the mission statment. what made me keep on is the community support! 

Again a big Thank You...

---

### Post by tseliot on 2006-08-13
> **PendragonUK said:**
> [size="6"]
Thank You[/size]

It is now working :-D 

Serousely though your help has taught me so much, I have been playing around with Linux on and off for years. I have tryed so mainy distros over that time. What drew me to ubuntu was the mission statment. what made me keep on is the community support! 

Again a big Thank You...

You're welcome ;) . I'll add this to the problems section of my guide so that all the users with the same problem as yours can find the same solution.

---

