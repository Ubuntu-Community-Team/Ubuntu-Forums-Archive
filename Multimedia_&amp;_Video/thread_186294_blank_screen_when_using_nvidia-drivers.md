---
title: "blank screen when using nvidia-drivers"
date: 2006-06-01
forum: Multimedia &amp; Video
---

### Post by chameleon_789 on 2006-06-01
ok, I've tried both method 1 and 2 of tseliots howto, and neither of them seem to work.

Using method 1, after using nvidia-xconfig to change the xorg.conf file, I get a blank screen and have to boot into recovery mode and change the driver entry to nv in order to use X. 

Using method 2, when X starts up, I get a message saying that the nvidia module can't be found, after which I copy the modules from /usr/lib/xorg/lib* (an error in the nvidia installer?) to the right directorys, giving me *yet again* a blank screen when restarting X ](*,). 

Using the nvidia installer without any extra options also yields no results. With breezy it was working fine, what's changed in the new version?

I'm using a dapper 6.06 rc live cd which is installed and is fully updated.

My xorg.conf :
```
Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
# Driver         "nvidia"
    Driver         "nv"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
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

### Post by tonyr on 2006-06-01
Try removing the **splash** option in the **kernel** command
line in your **/boot/grub/menu.lst** file.  You have to be root to do this.
In a terminal do **sudo <your-favorite-editor> /boot/grub/menu.lst**

---

### Post by chameleon_789 on 2006-06-01
No luck :( nothing in the nvidia and dmesg log files either.. I would provide some more info but I have no idea what the problem is! The driver seems to have installed fine after some tinkering, but X continually refuses to work with it :|

---

### Post by bluevoodoo1 on 2006-06-01
I can't help to notice there is no BusID in your Section "Device" area...

Snippet from my xorg.conf...

Section "Device"
	Identifier	"NVIDIA FX 5500"
	Driver		"nvidia"
	BusID		"PCI:2:9:0"

you can find your BusID with the command ```
lspci
```

It'll look something like this...
```
0000:02:09.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
```


If you run ```
sudo dpkg-reconfigure xserver-xorg
``` and let it automatically search for hardware, it might put the BusID in your xorg.conf for you.

---

### Post by tonyr on 2006-06-01
[QUOTE=chameleon_789]No luck :( nothing in the nvidia and dmesg log files either.. I would provide some more info but I have no idea what the problem is! The driver seems to have installed fine after some tinkering, but X continually refuses to work with it :|[/QUOTE]

when you say **nvidia** log file, are you talking about **/var/log/Xorg.0.log**?
Could you QUOTE or attach that file here, please?

---

### Post by chameleon_789 on 2006-06-02
Adding my BusID doesn't work, but thanks for the tip anyway.

When I said nvidia log file, I meant the installer which didn't say anything about a messed up compile, etc. 

Here's my Xorg.0.log file :

> X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux chameleon-ubuntu 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun  2 11:48:32 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/
:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" #
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
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0760 card 1849,0760 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1039,0002 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0964 card 0000,0000 rev 36 class 06,01,00 hdr 80
(II) PCI: 00:02:5: chip 1039,5513 card 1849,5513 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 1849,7001 rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 1849,7001 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:2: chip 1039,7001 card 1849,7001 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:3: chip 1039,7002 card 1849,7002 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0900 card 1849,0900 rev 90 class 02,00,00 hdr 00
(II) PCI: 00:0a:0: chip 1102,0004 card 1102,2007 rev 04 class 04,01,00 hdr 80
(II) PCI: 00:0a:2: chip 1102,4001 card 1102,0010 rev 04 class 0c,00,10 hdr 80
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,00f1 card 0000,0000 rev a2 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xeaa00000 - 0xeeafffff (0x4100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xca900000 - 0xea8fffff (0x20000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] rev 162, Mem @ 0xed000000/24, 0xd0000000/28, 0xec000000/24, BIOS @ 0xeeae0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
	[1] -1	0	0xfebff800 - 0xfebfffff (0x800) MX[B]
	[2] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[3] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[4] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[5] -1	0	0xfebf7000 - 0xfebf7fff (0x1000) MX[B]
	[6] -1	0	0xfebf6000 - 0xfebf6fff (0x1000) MX[B]
	[7] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[8] -1	0	0xeeae0000 - 0xeeafffff (0x20000) MX[B](B)
	[9] -1	0	0xec000000 - 0xecffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ec00 - 0x0000ec3f (0x40) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
	[1] -1	0	0xfebff800 - 0xfebfffff (0x800) MX[B]
	[2] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[3] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[4] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[5] -1	0	0xfebf7000 - 0xfebf7fff (0x1000) MX[B]
	[6] -1	0	0xfebf6000 - 0xfebf6fff (0x1000) MX[B]
	[7] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[8] -1	0	0xeeae0000 - 0xeeafffff (0x20000) MX[B](B)
	[9] -1	0	0xec000000 - 0xecffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ec00 - 0x0000ec3f (0x40) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
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
	[4] -1	0	0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
	[5] -1	0	0xfebff800 - 0xfebfffff (0x800) MX[B]
	[6] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[7] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[8] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[9] -1	0	0xfebf7000 - 0xfebf7fff (0x1000) MX[B]
	[10] -1	0	0xfebf6000 - 0xfebf6fff (0x1000) MX[B]
	[11] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[12] -1	0	0xeeae0000 - 0xeeafffff (0x20000) MX[B](B)
	[13] -1	0	0xec000000 - 0xecffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000ec00 - 0x0000ec3f (0x40) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
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


So... it's hanging when it gets to LoadModule "nvidia".. I'm assuming the module's loading but it can't find a library of some sort? Any ideas? (This is with method 1 of tseliots howto, literally just )
```
apt-get install nvidia-glx linux-restricted-modules-`uname -r`
```

---

### Post by tseliot on 2006-06-02
Ok, let's try to diagnose the error:

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

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then
```
sudo /etc/init.d/gdm start (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm start (if you use KDM)
```


Post the content of that file (which you can find under /home/your_username/Xorg.0.log )

---

### Post by chameleon_789 on 2006-06-02
Well I followed your steps pretty much exactly, except on a hunch I deleted the Xorg.0.* files in /var/log/ beforehand so I could tell if one had been created or not. 

At "startx -- -verbose 5 -logverbose 5", I get a blank screen, which doesn't accept keypresses, ctrl+alt+F1 and ctrl+c don't work (the bongo sound which happens at the login screen doesn't sound either, so it's hanging before it reaches there). I had to force a reboot. After that, I rebooted into recovery mode and checked out /var/log. Xorg.0.log hadn't been created, but when I change my xorg.conf from "nvidia" to "nv" and start back up, I get a fresh log file, which doesn't mention anything about the nvidia driver.

I've tried both method 1 and method 2 from a clean install and both of them give me this result. Am I doing something wrong, I've followed the Dapper tutorial word for word (where it applies) and it keeps hanging?

---

### Post by tseliot on 2006-06-02
Did Tonyr suggestion work?

If not, you might try passing "noapic" at boot. If you want to know how to pass a parameter at boot you can have a look at the following guide:
[http://ubuntuforums.org/showthread.php?t=75281]("http://ubuntuforums.org/showthread.php?t=75281")

Look for the part where it says:
```
OTHERWISE

b) If you have installed Ubuntu...
```

---

### Post by tonyr on 2006-06-02
What is your hardware configuration? This whouldn't by
any chance be some kind of Dell machine, would it?

I had problems with my Dell Inspiron 2650, and I found some help at
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14]("http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14")
by searching on my machine name/model.  If all else fails....

---

### Post by chameleon_789 on 2006-06-02
Well... none of the previous suggestion worked.. I *finally* got it to work however with the line 

**Option "NvAGP" "0"**

in my xorg.conf. Thanks for all the advice anyway :) I didn't really have much to go on, the problem still occured after blacklisting agpgart so I wasn't sure if it was an agp problem or not.

But... now I know it's an agp problem, is there anyway to enable agp acceleration? 
**cat /proc/driver/nvidia/agp/status** outputs Status : disabled

---

### Post by chameleon_789 on 2006-06-02
Quick update : I've gone through the usual steps to enable NvAGP (blacklisted sis_agp, amd64_agp and agpgart) but agpgart loads anyway, it looks as though the nvidia driver depends on it(?)
> chameleon@chameleon-ubuntu:~$ lsmod | grep agp
agpgart                34888  1 nvidia
There's a module **nvidia_agp** lying around, is there a way to swap that for agpgart, or is agp only supported through agpgart (I would have thought not)?

---

### Post by tseliot on 2006-06-02
[QUOTE=chameleon_789]Quick update : I've gone through the usual steps to enable NvAGP (blacklisted sis_agp, amd64_agp and agpgart) but agpgart loads anyway, it looks as though the nvidia driver depends on it(?)

There's a module **nvidia_agp** lying around, is there a way to swap that for agpgart, or is agp only supported through agpgart (I would have thought not)?[/QUOTE]
Try setting NvAGP to 1 or 3 and see if anything changes

---

### Post by chameleon_789 on 2006-06-02
I got it :) 

Turns out agpgart is incompatible with SIS-760 motherboards (it detected my AGP aperture as 4meg), renaming sis-agp.ko to sis-agp.ko.bak stopped X hanging and now everything's running smoothly with AGPGART acceleration enabled. 

Thanks for the help everyone. For the record, setting NvAGP to 1 worked, but didn't use acceleration, and setting it to 3 gave me the same hang.. now with sis-agp renamed X works fine with NvAGP set to 3.

---

### Post by obsydian on 2006-06-02
I'm having a similar problem I think.  When I install the nvidia drivers (method 1), the screen just blanks (power save mode) when X starts.  It's not hanging, since I can hear the sound, and if I log in it seems to proceed fine except for the blank screen.  I can Ctrl-Alt-F1 to get to a terminal, and that shows up fine, but when I try to switch to X it just blanks again.

I just did a clean install, and I'm running a nForce2 board.  I've tried everything mentioned in this thread, but no luck.

---

### Post by obsydian on 2006-06-02
Had to force it to output over DVI.  For some reason it wasn't autodetecting right...

---

### Post by centered effect on 2006-06-03
[]("http://www.ubuntuforums.org/member.php?u=114777") Thank you for the solution to a similar problem I was having with my sis760 board and my nvidia card!  I now have acceleration

---

### Post by ZoekDribbel on 2006-07-03
Oh YES! This was what I was looking for! :D :D 

It works like a charm! \\:D/ 

* rename the stupid sis_agp thingy
* set to nvidia 
* enjoy! and barf on SiS

Thank you so much, i couldn't figure that out on my own!

---

