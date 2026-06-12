---
title: "Kernel-Updates always mess with the Xserver"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by derfinsterling on 2007-05-28
This is so annoying.

Everytime I install Ubuntu, the xserver won't start. Everytime I have to run that old dkpg-reconfigure thing, then work around endlessly to set up my NVIDIA card until it's finally done and I can work again.

Then comes a kernel-update - repeat the whole thing.
I upgrade to Feisty - repeat the whole thing.
I install the newest updates, see too late that there's a new kernel - repeat the whole damn thing *again*.

This time I didn't fret because I wisely made two extra backups of my working xorg.conf file. So I thought I'd just copy it over the one that isn't working and that would be that.
Of course it wasn't.

I don't get it. I don't want to spend 2 hours+ on my windows-notebook browsing the internet, trying to remember what worked the last time around. Is it really that much to ask that the upgrades don't mess around with my xserver settings?
Is NVIDIA really that hard to implement under Linux?

I've got it running now, using the old dkpg-reconfigure again, but this time I had to use automatix to install the NVIDIA-drivers.
Then run nvidia-settings as sudo so that the changes to the xorg-file are actually written to it.
I'm pretty sure when I re-boot I'll have to repeat that whole damn thing again.

Sorry for the rambling rant - but maybe I'm doing something so obviously wrong that one of you fine gentlemen can show me the error?
Thanks in advance.

---

### Post by zaphodbeeblebrox on 2007-05-28
I agree with you here. My xserver always gets $%^#ed up too after kernel updates. I don't think they have much control over this though seeing as how nvidia isn't on the opensource bandwagon. I have played with other distros and this one seems to be the shiznit when it comes to user friendliness. I used to use mandrake and it was decent but there was a lot less support for  scripts that do the work for you. At least that was my experience. I have to thank you for posting the dpkg-reconfigure thingy.....i forgot what i did last time too. I do however, remember throwing a fit and stomping the floor a couple of times!

---

### Post by tseliot on 2007-05-28
You might solve the problem in different ways:
1) install "linux-generic" and nvidia-glx so that every time the kernel is updated also the restricted-modules are updated (this is the method which is officially supported by Ubuntu).

2) Install the driver through Envy. Then if the Xserver crashes after an update just run Envy's textual installer (sudo envy -t) and Envy will reinstall the driver and start the Xserver for you.

---

### Post by hanzomon4 on 2007-05-28
You need to install the drivers using the nvidia-glx package and the restricted-modules package to avoid this problem. The problem is that you are not installing the drivers correctly, i.e. it's your fault. I believe that we have 2 other nvidia-glx packages (nvidia-glx-legacy)(nvidia-glx-new), I had to use new. Install the restricted modules for your kernel version and everything should be ok.

---

### Post by Nythain on 2007-05-28
yeah, it seriously sounds like you are manually installing the drivers provided from nvidia's site and not the nvidia-glx packages from the repos...
problem is, when you install the run file from nvidia, it compiles the module against your current kernel, so when you upgrade your kernel, its very confused and thus doesnt work untill you reinstall against the new kernel.
if you install via nvidia-glx (or nvidia-glx-new or nvidia-glx-legacy, depending on card) and the restricted modules package, then those get updated at the same time as the kernel, piece of cake... feisty has made it even easier by giving you an enable restricted drivers option somewhere in the distro (i dont know, i use kubuntu and dont have this option anywbhere)

---

### Post by derfinsterling on 2007-05-28
I did install the nvidia-glx-drivers originally when updating to Feisty. Since that did squat, I pretty much had to install using the file from the nvidia-site.

---

### Post by Nythain on 2007-05-28
not sure why the nvidia-glx package didnt do squat, works wonders for majority of the ubuntu world... i havent had a single update to my machine, from dapper to edgy to feisty that jacked up my xorg.conf file (or altered it in any way at all actually)... and like said above, as long as you install the package from nvidia's site, you are going to have to get used to re-installing the drivers after every kernel upgrade

---

### Post by derfinsterling on 2007-05-28
I just checked and I currently have the nvidia-glx-new package installed. I've got a Geforce 8800 GTS, so that should be fine. 
I tried "sudo nvidia-glx-config enable" but got the error message:
> Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
But - the driver section in the xorg.conf file is:
> 
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
EndSection


Can I install other packages, like just nvidia-glx? Will that take care of other discrepancies? Messing with the md5sum doesn't appeal too much to me...

---

### Post by WinterWeaver on 2007-05-28
.... mine didn't beak ... desktop effects and everything is still working 100% ... sounds like you manually installed it or something.

---

### Post by derfinsterling on 2007-05-28
Seems to be a general problem with 8800 GTS:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/107831](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/107831)

---

### Post by trak87 on 2007-05-28
I'm also bummed that upgrading the kernel breaks the nvidia graphics driver for me. I did not install the graphics driver from the nvidia  website however so I'm not sure how to fix the situation. I tried the suggestion to install "linux-generic" and nvidia-glx (nvidia-glx-new in my case), rebooted and reran "sudo dpkg-reconfigure xserver-xorg" selecting the nvidia option, but this did not work. I also installed the "generic" kernel...

Can somebody help? My card is a PNY Geforce 6200.

---

### Post by hanzomon4 on 2007-05-28
Well let me think... I had this issue after switching to the nvidia-glx in the repos after having used the run file from the nvidia site. Did you use the envy script by any chance? If not great. Post the output from this command ```
 cat /var/log/Xorg.0.log
``` it should tell us why X is not starting,

---

### Post by tseliot on 2007-05-29
> **trak87 said:**
> I'm also bummed that upgrading the kernel breaks the nvidia graphics driver for me. I did not install the graphics driver from the nvidia  website however so I'm not sure how to fix the situation. I tried the suggestion to install "linux-generic" and nvidia-glx (nvidia-glx-new in my case), rebooted and reran "sudo dpkg-reconfigure xserver-xorg" selecting the nvidia option, but this did not work. I also installed the "generic" kernel...

Can somebody help? My card is a PNY Geforce 6200.

try this command:
```
sudo apt-get install --reinstall linux-restricted-modules-`uname -r`
```

---

### Post by Tux Aubrey on 2007-05-29
> **tseliot said:**
> try this command:
```
sudo apt-get install --reinstall linux-restricted-modules-`uname -r`
```

This worked for me (with a GeForce 6600 LE).  

This was the first kernel update on a clean feisty install that was fairly fraught getting the nVidia driver to work originally.

I am now going to go and tattoo that command on my arm.

---

### Post by derfinsterling on 2007-05-29
> **hanzomon4 said:**
> Well let me think... I had this issue after switching to the nvidia-glx in the repos after having used the run file from the nvidia site. Did you use the envy script by any chance? If not great. Post the output from this command ```
 cat /var/log/Xorg.0.log
``` it should tell us why X is not starting,

Here it is:
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux scubuntu 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue May 29 23:18:42 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(WW) The directory "/usr/X11R6/lib/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/usr/X11R6/lib/X11/fonts/Type1".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/X11R6/lib/X11/fonts/Type1").
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "Xinerama" "0"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,03a3 card 0000,0000 rev a2 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,03ac card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,03aa card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,03a9 card 0000,0000 rev a1 class 05,00,00 hdr 00
(II) PCI: 00:00:4: chip 10de,03ab card 0000,0000 rev a1 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,03a8 card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,03b5 card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,03b4 card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,03ad card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:1: chip 10de,03ae card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:2: chip 10de,03af card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:3: chip 10de,03b0 card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:4: chip 10de,03b1 card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:5: chip 10de,03b2 card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:6: chip 10de,03b3 card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,03b6 card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:02:1: chip 10de,03bc card 0000,0000 rev a1 class 05,00,00 hdr 00
(II) PCI: 00:02:2: chip 10de,03ba card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:03:0: chip 10de,03b7 card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 10de,03b8 card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:06:0: chip 10de,03b9 card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 10de,03bb card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0270 card 1043,81bc rev a2 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0260 card 1043,81bc rev a3 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0264 card 1043,81bc rev a3 class 0c,05,00 hdr 80
(II) PCI: 00:0a:2: chip 10de,0272 card 1043,81bc rev a3 class 05,00,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,026d card 1043,81bc rev a3 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,026e card 1043,81bc rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0265 card 1043,81bc rev a1 class 01,01,8a hdr 00
(II) PCI: 00:0e:0: chip 10de,0266 card 1043,81bc rev a1 class 01,01,85 hdr 00
(II) PCI: 00:0f:0: chip 10de,0267 card 1043,81bc rev a1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:1: chip 10de,026c card 1043,8249 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:14:0: chip 10de,0269 card 1043,8221 rev a3 class 06,80,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0193 card 3842,e815 rev a2 class 03,00,00 hdr 00
(II) PCI: 04:00:0: chip 197b,2360 card 1043,8208 rev 02 class 01,06,01 hdr 00
(II) PCI: 05:08:0: chip 1106,3044 card 1043,81fe rev c0 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:3:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:5:0), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfdf00000 - 0xfdffffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:6:0), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xfdc00000 - 0xfdcfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:7:0), (0,4,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfd900000 - 0xfd9fffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xfd800000 - 0xfd8fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:16:0), (0,5,5), BCTRL: 0x0200 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xfdb00000 - 0xfdbfffff (0x100000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xfda00000 - 0xfdafffff (0x100000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x0193) rev 162, Mem @ 0xfa000000/24, 0xe0000000/28, 0xf8000000/25, I/O @ 0xcf00/7, BIOS @ 0xfbfe0000/17
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
(II) Active PCI resource ranges:
	[0] -1	0	0xfdbff000 - 0xfdbff7ff (0x800) MX[B]
	[1] -1	0	0xfd9fe000 - 0xfd9fffff (0x2000) MX[B]
	[2] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[3] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[4] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[5] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[6] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[7] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[8] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[9] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000bf00 - 0x0000bf7f (0x80) IX[B]
	[13] -1	0	0x0000db00 - 0x0000db0f (0x10) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[15] -1	0	0x0000dd00 - 0x0000dd07 (0x8) IX[B]
	[16] -1	0	0x0000de00 - 0x0000de03 (0x4) IX[B]
	[17] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]
	[18] -1	0	0x0000f200 - 0x0000f207 (0x8) IX[B]
	[19] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[20] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[21] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[22] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[23] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[24] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[25] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[26] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[27] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[28] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[29] -1	0	0x0000fd00 - 0x0000fd0f (0x10) IX[B]
	[30] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[31] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[32] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfdbff000 - 0xfdbff7ff (0x800) MX[B]
	[1] -1	0	0xfd9fe000 - 0xfd9fffff (0x2000) MX[B]
	[2] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[3] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[4] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[5] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[6] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[7] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[8] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[9] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000bf00 - 0x0000bf7f (0x80) IX[B]
	[13] -1	0	0x0000db00 - 0x0000db0f (0x10) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[15] -1	0	0x0000dd00 - 0x0000dd07 (0x8) IX[B]
	[16] -1	0	0x0000de00 - 0x0000de03 (0x4) IX[B]
	[17] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]
	[18] -1	0	0x0000f200 - 0x0000f207 (0x8) IX[B]
	[19] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[20] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[21] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[22] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[23] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[24] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[25] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[26] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[27] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[28] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[29] -1	0	0x0000fd00 - 0x0000fd0f (0x10) IX[B]
	[30] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[31] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[32] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B](B)
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
	[4] -1	0	0xfdbff000 - 0xfdbff7ff (0x800) MX[B]
	[5] -1	0	0xfd9fe000 - 0xfd9fffff (0x2000) MX[B]
	[6] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[7] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[8] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[12] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000bf00 - 0x0000bf7f (0x80) IX[B]
	[19] -1	0	0x0000db00 - 0x0000db0f (0x10) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[21] -1	0	0x0000dd00 - 0x0000dd07 (0x8) IX[B]
	[22] -1	0	0x0000de00 - 0x0000de03 (0x4) IX[B]
	[23] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]
	[24] -1	0	0x0000f200 - 0x0000f207 (0x8) IX[B]
	[25] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[26] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[27] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[28] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[29] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[30] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[31] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[32] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[33] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[34] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[35] -1	0	0x0000fd00 - 0x0000fd0f (0x10) IX[B]
	[36] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[37] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[38] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B](B)
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9755
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9755
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  1.0-9755  Mon Feb 26 23:23:13 PST 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdbff000 - 0xfdbff7ff (0x800) MX[B]
	[5] -1	0	0xfd9fe000 - 0xfd9fffff (0x2000) MX[B]
	[6] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[7] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[8] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[12] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000bf00 - 0x0000bf7f (0x80) IX[B]
	[19] -1	0	0x0000db00 - 0x0000db0f (0x10) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[21] -1	0	0x0000dd00 - 0x0000dd07 (0x8) IX[B]
	[22] -1	0	0x0000de00 - 0x0000de03 (0x4) IX[B]
	[23] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]
	[24] -1	0	0x0000f200 - 0x0000f207 (0x8) IX[B]
	[25] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[26] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[27] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[28] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[29] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[30] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[31] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[32] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[33] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[34] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[35] -1	0	0x0000fd00 - 0x0000fd0f (0x10) IX[B]
	[36] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[37] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[38] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdbff000 - 0xfdbff7ff (0x800) MX[B]
	[5] -1	0	0xfd9fe000 - 0xfd9fffff (0x2000) MX[B]
	[6] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[7] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[8] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[9] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[10] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[11] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[12] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000bf00 - 0x0000bf7f (0x80) IX[B]
	[22] -1	0	0x0000db00 - 0x0000db0f (0x10) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[24] -1	0	0x0000dd00 - 0x0000dd07 (0x8) IX[B]
	[25] -1	0	0x0000de00 - 0x0000de03 (0x4) IX[B]
	[26] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]
	[27] -1	0	0x0000f200 - 0x0000f207 (0x8) IX[B]
	[28] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[29] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[30] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[31] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[32] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[33] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[34] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[35] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[36] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[37] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[38] -1	0	0x0000fd00 - 0x0000fd0f (0x10) IX[B]
	[39] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[40] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[41] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "MetaModes" "1280x960 +0+0; 800x600 +0+0; 640x480 +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 8800 GTS at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 327680 kBytes
(--) NVIDIA(0): VideoBIOS: 60.80.0d.00.15
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8800 GTS at PCI:1:0:0:
(--) NVIDIA(0):     BenQ FP93GX (DFP-1)
(--) NVIDIA(0): BenQ FP93GX (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): BenQ FP93GX (DFP-1): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x960+0+0"
(II) NVIDIA(0):     "800x600+0+0"
(II) NVIDIA(0):     "640x480+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 960
(--) NVIDIA(0): DPI set to (85, 81); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] 0	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfdbff000 - 0xfdbff7ff (0x800) MX[B]
	[8] -1	0	0xfd9fe000 - 0xfd9fffff (0x2000) MX[B]
	[9] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[10] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[11] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[12] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[13] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[14] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[15] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[16] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[17] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] 0	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000bf00 - 0x0000bf7f (0x80) IX[B]
	[26] -1	0	0x0000db00 - 0x0000db0f (0x10) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[28] -1	0	0x0000dd00 - 0x0000dd07 (0x8) IX[B]
	[29] -1	0	0x0000de00 - 0x0000de03 (0x4) IX[B]
	[30] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]
	[31] -1	0	0x0000f200 - 0x0000f207 (0x8) IX[B]
	[32] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[33] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[34] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[35] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[36] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[37] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[38] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[39] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[40] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[41] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[42] -1	0	0x0000fd00 - 0x0000fd0f (0x10) IX[B]
	[43] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[44] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[45] -1	0	0x0000cf00 - 0x0000cf7f (0x80) IX[B](B)
	[46] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[47] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x960+0+0"
(--) NVIDIA(0): No video decoder detected
(II) NVIDIA(0): Setting mode "1280x960+0+0"
(--) NVIDIA(0): No video decoder detected
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
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
(**) Option "CoreKeyboard"
(**) Keyboard0: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Mouse0: Device: "/dev/psaux"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: Core Pointer
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded
```

---

### Post by NumberOne on 2007-05-29
My xserver go hosed with the new kernel update.  I had previously install the nvidia drivers using envy.  I tried installing the drivers using synaptic and it didnot work.  I tried envy again and worked partially.  After envy, I had no banner bars on any window.  I had to manually add a command to the nvida config from the terminal to get them back.  It was something like "sudo nvidia-config --add" and then a bunch of directives.  I found this through  the search function.

---

### Post by Justin Trouble on 2007-05-30
I have the nvidia-glx-new package installed which was working fine with kernel 2.6.20-**15**-generic, but when I rebooted after a kernel upgrade to 2.6.20-**16**-generic the nvidia kernel module failed to load, dropping me to the black command line login screen.

I found the answer in the dependencies of nvidia-glx-new.

nvidia-glx-new requires nvidia-kernel-1.0.9755 which is found in linux-restricted-modules-2.6.20-**x**-generic.

linux-restricted-modules-2.6.20.**15**-generic was installed but linux-restricted-modules-2.6.20.**16**-generic was not!

I installed linux-restricted-modules-2.6.20.**16**-generic and the nvidia kernel module loads and X starts successfully.

I would have thought linux-restricted-modules-2.6.20.**16**-generic would be automatically upgraded along with the kernel update?

---

### Post by handy on 2007-05-30
I've learned to wait for a few days after a kernel update is released on Ubuntu, before installing the update.  There seems to always be a delay in getting the restricted modules released, & it gives me some time to check the forums & see if there are any other problems with the update before I commit to it.

If everything is working ok, there is no need to rush in & break it! ;)

---

### Post by trak87 on 2007-05-30
Thanks. I got it working. :p

---

### Post by rickdog on 2007-05-30
Help! I'm dead in the water here. I've seen a few posts regarding this issue with x crashing after the kernel upgrade. I don't know what to do. I've tried some of the commands listed but nothing seems to work. I even get "Couldn't find package linux-restricted-modules", huh?

Anyway, I don't even know how to post anything from my other computer, which is the one down, but it basically runs through what the original post said.

In addition it says (after the Failed to load NVIDIA kernel module! part):

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
         after 0 requests (0 know processed) with 0 events remaining.

what the %#@&?

I'm afraid that the more I try to tweak with it the worse it gets.

wait, I reran gdm and I'm seeing that it also says:

(EE) Failed to load module "wfb" (module does not exist, 0)

Then it says the FATAL: Error running install command for nvidia

and ends with "Screens found, but non have a usable configuration"

Help

---

### Post by Justin Trouble on 2007-05-31
> **rickdog said:**
> Help! I'm dead in the water here. I've seen a few posts regarding this issue with x crashing after the kernel upgrade. I don't know what to do. I've tried some of the commands listed but nothing seems to work. I even get "Couldn't find package linux-restricted-modules", huh?

Anyway, I don't even know how to post anything from my other computer, which is the one down, but it basically runs through what the original post said.

In addition it says (after the Failed to load NVIDIA kernel module! part):

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
         after 0 requests (0 know processed) with 0 events remaining.

what the %#@&?

I'm afraid that the more I try to tweak with it the worse it gets.

wait, I reran gdm and I'm seeing that it also says:

(EE) Failed to load module "wfb" (module does not exist, 0)

Then it says the FATAL: Error running install command for nvidia

and ends with "Screens found, but non have a usable configuration"

Help

If X / Gnome / KDE worked before a kernel update then it's unlikely to be your X configuration (xorg.conf). You can select a previous kernel version at boot time to test.

To check/install the correct linux-restricted-modules package for your **running** kernel is available/installed use this command:
```
sudo apt-get install linux-restricted-modules-`uname -r`
```

I'm using Feisty.

---

### Post by rickdog on 2007-05-31
Okay, I'm using Feisty too. For now I found a work-around. I dpkg-reconfigured and set the driver to VESA and was able to startx again. I guess now I'll try to work with Envy to reinstall the nvidia drivers.

As I said before, I kept getting that it was not able to find the linux-restricted-modules. However, I hadn't run sudo atp-get update first, so that might have had something to do with it. I don't know.

Also, has anyone noticed that with this new kernel, the harddrives are back to hda1 and such instead of sda1? What's up with that?

Thanks for the help!

---

### Post by tim71 on 2007-06-19
When Nvidia drivers have been installed manually from nvidia site, then it is not necessary to reinstall whole  driver package. Just run 
```
sudo sh <driver package location> -K
```
from command line to recompile the kernel module.

After that
```
sudo modprobe nvidia
sudo /etc/init.d/gdm restart
```
should bring you back to login screen as normally.

---

### Post by derfinsterling on 2007-06-23
Thanks - I'll try that.

---

