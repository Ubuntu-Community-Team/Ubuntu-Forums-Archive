---
title: "No GUI, suspect ATI video card problem"
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by burgerearl on 2007-11-25
I marked my thread in the Installation forum solved after I successfully used the text installer to get installed. It was located at [http://ubuntuforums.org/showthread.php?t=622307](http://ubuntuforums.org/showthread.php?t=622307)

Since I'm having issues that I think are video card related, I'm posting here instead.

Summary:

AMD Athlon64 3000+
Radeon 9200
1GB Ram

I get no GUI after a successful boot. I can use Ctrl Alt F1 to get a command line. I have tried reconfiguring xorg to use both the ati and vesa driver:

ati gives the errors posted in the other thread. 
Vesa gets the ubuntu boot sound but still no GUI. 

Ctrl Alt F1 using vesa driver shows the error "screen 0 is not DRI capable"

Any suggestions? I'm also a complete newbie....

---

### Post by zbyszek_zbl on 2007-11-26
As I can understand you have only text mode? Do you have an Internet connection? If so try:
CODE:
wget [http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu1_all.deb)
sudo dpkg -i envy_0.9.9-0ubuntu1_all.deb
sudo envy -t
and than select option remove ati driver
After this run envy again and select - install ati driver
It should install and configure for you proper "closed" driver from ATI

---

### Post by Yellow Pasque on 2007-11-26
Before doing the envy thing, post your xorg.conf because if you're still getting the same "no device found" errors, you probably just need to edit that.

Also post the result of this command sequence:
```
sudo update-pciids
lspci | grep "VGA"
```

---

### Post by markoloka on 2007-11-26
Are you using fglrx or radeon driver? Which version?
Have you tried to edit  xorg w/

Section "DRI"
        Mode 0666
EndSection

---

### Post by burgerearl on 2007-11-26
Wow, thanks for all the responses. Sorry I couldn't get back to you sooner.

@temujin

lspci | grep "VGA" gave the following:

00:00.0 VGA compatible controller: NVidia/SGS Thomson (JointVenture) Riva128 (rev 22)
01:00.0 VGA Compatible controller: ATI technologies Inc RV280 [Radeon 9200 SE] (rev 01)

I have a second graphics card (PCI) that's not in use, to clarify if two results weren't expected.

I searched a little but couldn't find an easy answer to this:

can I output the result of a command to a text file on my NTFS partition or on my external hard drive? That would make it a lot easier to post results when I have to switch back to Windows to do so...

@zbyzek
Also, I tried the first step of the envy instructions, but I got an error that I was missing a bunch of dependencies. I know that I've seen a command to download and install dependencies, but I couldn't find that by searching either. Can anyone fill me in on that?

@markoloka

the only thing I've done to edit xorg at all (I think) is running the command:

dpkg-reconfigure xserver-xorg

and then taking most defaults but changing resolutions or drivers (vesa/ati)

Thanks!

---

### Post by burgerearl on 2007-11-28
I've tried several more things to get this working:

I switched my ATI card for an Nvidia v9250. Same results, except that the splash screen with the loading bar was displayed (usually the monitor gives an error during that time, then goes black after the splash screen is done).

I also tried removing the extra PCI video card I had (not in use). Now, boot hangs on "running local boot scripts"

I tried putting the PCI card back in, same results.

The boot processes go up to boot scripts, then the screen flashes between that list and a black screen about 5 times, then just hangs showing the list of processes (boot scripts being the last one)

Additionally, I'm now not seeing the boot screen (again)

Any ideas?

---

### Post by Yellow Pasque on 2007-11-28
That means the X server isn't starting. Please post your /etc/X11/xorg.conf file.

Is your Windows disk SATA or PATA? If it's a PATA disk and set as the master, type;
```
sudo fdisk -l /dev/hda
```
If it's SATA, replace hda with sda or sdb.
You're looking for the name of your ntfs partition. So if it ends up being hda1, you would type:

```
sudo mkdir ~/windisk
sudo mount -t ntfs /dev/hda1 ~/windisk

```

Now you can write the file to your Windows drive.

---

### Post by burgerearl on 2007-11-28
My xorg.conf is posted below. However, something else has now happened that makes me suspect that I have some problem with incompatible hardware: 

I tried to use the system rescue cd to restore an image of my windows partition that I made before installing Ubuntu (because of problems posted here: [http://ubuntuforums.org/showthread.php?t=625263]("http://ubuntuforums.org/showthread.php?t=625263") 
When I used the sys rescue cd to partition my hard drive to install Ubuntu, I had a gui. Now I don't. I *am* on a different monitor now, however, I have two and neither is working. I am at a loss as to what is going on.

Anyway, the xorg.conf for Ubnutu is as follows:
```

# xorg.conf (xorg X Window System server configuration file)

#

# This file was generated by dexconf, the Debian X Configuration tool, using

# values from the debconf database.

#

# Edit this file with caution, and see the xorg.conf manual page.

# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:12:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

Hope this helps, thanks.

---

### Post by Yellow Pasque on 2007-11-29
Hello again. Make your xorg.conf look like this:
```
Section "Module"
	Load		"dbe"
	Load		"extmod"
	Load		"fbdevhw"
	Load		"glx"
	Load		"record"
	Load		"freetype"
	Load		"type1"
	Load		"dri"
        Load            "i2c"
        Load            "vbe"
EndSection

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "Device"
	Identifier	"Generic Video Card"
	Driver		"ati"
	BusID		"PCI:0:12:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

You may need to add resolutions in the screen section. Also, you may need to change the BusID in the Device section. Run the following command:
```
sudo update-pciids; lspci | grep "VGA"
```
If it returns "01:12.00 VGA compatible...", then all is well. However, if the numbers are different, then you need to change the BusID parameter to match them.

---

### Post by burgerearl on 2007-11-29
I copied the xorg.conf you posted to /etc/X11

I did need to change the BusID to 01:00.0

I had to use the system rescue CD to do it because of the boot script problem described above. The first time booting Ubuntu after copying, it booted directly to a command prompt (asking for logon). I tried startx after logging on, but got the same "no screens found error" again.

The next two reboots hung on "loading boot scripts" again.

So I'm not sure, did that help?

---

### Post by Yellow Pasque on 2007-11-29
You probably edited the copy in memory working from the CD.
DO NOT boot off the CD. Boot off the HD and press "Ctrl+Alt+F1" when it hangs to get to a terminal. Login.
sudo nano /etc/X11/xorg.conf

---

### Post by burgerearl on 2007-11-29
I *think* that I couldn't even get a terminal last time I booted, but I'm not positive.

Regardless, I mounted my windows and ubuntu partitions with the rescue cd and copied your xorg.conf (which I saved on my NTFS partition):

```
mkdir /mnt/ubuntu
mkdir /mnt/windrive
mount /dev/sda1 /mnt/windrive
mount /dev/sda2 /mnt/ubuntu
cp /mnt/windrive/path to xorg/xorg.conf /mnt/ubuntu/etc/X11
```

I also just checked and confirmed that the xorg.conf on my ubuntu partition is the same as the one you posted.

---

### Post by Yellow Pasque on 2007-11-29
Well then, if you're still having problems, post your /var/log/Xorg.0.log so we can see what's stopping the show.

---

### Post by burgerearl on 2007-11-29
Thanks much! Here's the log:

```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux gerlach 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov 29 16:49:57 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3188 card 1043,80a3 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b188 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0a:0: chip 11ab,4320 card 1043,811a rev 13 class 02,00,00 hdr 00
(II) PCI: 00:0d:0: chip 1131,7133 card 1043,4845 rev f0 class 04,80,00 hdr 00
(II) PCI: 00:0f:0: chip 1106,3149 card 1043,80ed rev 80 class 01,04,00 hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1043,80ed rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1043,80ed rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1043,80ed rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 1043,80b0 rev 60 class 04,01,00 hdr 00
(II) PCI: 00:11:6: chip 1106,3068 card 0000,0000 rev 80 class 07,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1002,5964 card 1043,c008 rev 01 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,5d44 card 1043,c009 rev 01 class 03,80,00 hdr 00
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
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfd100000 - 0xfd6fffff (0x600000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xcff00000 - 0xefefffff (0x20000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV280 [Radeon 9200 SE] rev 1, Mem @ 0xe0000000/27, 0xfd600000/16, I/O @ 0xb000/8, BIOS @ 0xfd500000/17
(--) PCI: (1:0:1) ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) rev 1, Mem @ 0xd8000000/27, 0xfd400000/16
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
	[0] -1	0	0xfdf00000 - 0xfdf000ff (0x100) MX[B]
	[1] -1	0	0xfde00000 - 0xfde007ff (0x800) MX[B]
	[2] -1	0	0xfdd00000 - 0xfdd03fff (0x4000) MX[B]
	[3] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[4] -1	0	0xfd400000 - 0xfd40ffff (0x10000) MX[B](B)
	[5] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[6] -1	0	0xfd500000 - 0xfd51ffff (0x20000) MX[B](B)
	[7] -1	0	0xfd600000 - 0xfd60ffff (0x10000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[10] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[11] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[12] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[13] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[15] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[22] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfdf00000 - 0xfdf000ff (0x100) MX[B]
	[1] -1	0	0xfde00000 - 0xfde007ff (0x800) MX[B]
	[2] -1	0	0xfdd00000 - 0xfdd03fff (0x4000) MX[B]
	[3] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[4] -1	0	0xfd400000 - 0xfd40ffff (0x10000) MX[B](B)
	[5] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[6] -1	0	0xfd500000 - 0xfd51ffff (0x20000) MX[B](B)
	[7] -1	0	0xfd600000 - 0xfd60ffff (0x10000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[10] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[11] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[12] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[13] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[15] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[22] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
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
	[4] -1	0	0xfdf00000 - 0xfdf000ff (0x100) MX[B]
	[5] -1	0	0xfde00000 - 0xfde007ff (0x800) MX[B]
	[6] -1	0	0xfdd00000 - 0xfdd03fff (0x4000) MX[B]
	[7] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[8] -1	0	0xfd400000 - 0xfd40ffff (0x10000) MX[B](B)
	[9] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[10] -1	0	0xfd500000 - 0xfd51ffff (0x20000) MX[B](B)
	[11] -1	0	0xfd600000 - 0xfd60ffff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[19] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[21] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[27] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[28] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[29] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.0.2
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "i2c"(II) Module already built-in
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 6.7.195
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) ATI: ATI driver wrapper (version 6.7.195) for chipsets: mach64, rage128, radeon
(II) Primary Device is: PCI 01:00:0
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:0) found
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(EE) No devices detected.

Fatal server error:
no screens found

```

---

### Post by Yellow Pasque on 2007-11-29
> (WW) RADEON: No matching Device section for instance (BusID PCI:1:0:0) found

Can you double-check your xorg.conf and make sure you didn't change that value back somewhere along the way

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection
```

---

### Post by burgerearl on 2007-11-29
I did in fact have an error (PCI:01:00.0 instead of PCI:1:00.0), however correcting it didn't solve the problem: I got the same error (xorg.0.log has the same two warnings and the same error at the end).

Does it make a difference that my card is AGP and not PCI?

I have two other video cards I could try, is that worth the time?

---

### Post by nirishmodi on 2007-12-20
I am using a P4 PC and am having an AGP ATI Radeon 9200SE (rv280). UBUNTU loading bar stops a particular point everytime when I load the live CD and when I run it using my onboard graphics the it works fine. But with this I am not able to use its 3D features. What should I do?

---

### Post by burgerearl on 2007-12-20
You should probably start a new thread, your problem sounds a little different than mine. I don't really know anything about Ubuntu, but there's a lot of help available out there. Good luck!

---

