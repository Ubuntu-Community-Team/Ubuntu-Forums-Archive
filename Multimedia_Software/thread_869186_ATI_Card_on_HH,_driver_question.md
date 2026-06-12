---
title: "ATI Card on HH, driver question"
date: 2008-07-24
forum: Multimedia Software
---

### Post by NvidiaN on 2008-07-24
Hi, I'm very new to this but I'm going to try and give as much information as possible here with hopes that someone will be able to help me:

I'm relatively positive my graphics card (ATI IGP 320M) isn't being used by Ubuntu (Hardy Heron). Scrolling down a webpage lags the computer, which was never a problem in windows. I'm trying to install the drivers linked here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) however I'm running into issues, regardless of which "path" I choose.

The problem I'm having explicitly with the "easy route" is

"Enable accelerated the accelerated ATI graphics driver in the restricted-manager, then do:"

```
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
```

Initially I wasn't sure what the restricted manager was, but after googling it I found it was in system/administration/hardware drivers (I think). Well, there's no drivers listed here to enable, so I'm not really sure what to do.

```
 lspci -nn | grep VGA
```

Output looks like this:

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility U1 [1002:4336]

```
sudo vim /etc/X11/xorg.conf
```

Output looks like this for the video device section:

Section "Device"
Identifier "Configured Video Device"
EndSection


Again as I said I'm very new to this stuff, I'm used to windows where I can just go to ati.com and download a driver for card X for operating system Y...so if I'm missing a simple/easy step here I apologize (my current theory is that I'm missing the driver which I don't know where to download...since nothing is showing up in the driver manager). But any help would be very appreciated as the how to threads aren't doing the trick!

Thanks!

---

### Post by oneporter on 2008-07-24
I'm sorry you're having trouble with the ATI install.  I've had the same problem recently.  Sometimes it just won't show up on the Restricted Drivers Manager (You are correct in thinking that that is the same as System > Admin > Hardware Drivers).  I just reinstalled this morning (I'm trying to organize my hard drive and make a separate home partition, and I just deleted Windows for good!), and it didn't detect my card.  I ended up installing it wrong and then restarting and the hardware manager finally detected the correct thing.  I enabled, and it installed everything fine.

So, my advice is to make a backup of your xorg.conf, (cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak), and dive in, possibly mess it up, if so you can always use Gnome Failsafe by clicking Options > Sessions on the GDM (where you put in your password) or by restoring your original xorg.conf.  Anyway, hope that helps.

---

### Post by NvidiaN on 2008-07-25
> **oneporter said:**
> I'm sorry you're having trouble with the ATI install.  I've had the same problem recently.  Sometimes it just won't show up on the Restricted Drivers Manager (You are correct in thinking that that is the same as System > Admin > Hardware Drivers).  I just reinstalled this morning (I'm trying to organize my hard drive and make a separate home partition, and I just deleted Windows for good!), and it didn't detect my card.  I ended up installing it wrong and then restarting and the hardware manager finally detected the correct thing.  I enabled, and it installed everything fine.

So, my advice is to make a backup of your xorg.conf, (cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak), and dive in, possibly mess it up, if so you can always use Gnome Failsafe by clicking Options > Sessions on the GDM (where you put in your password) or by restoring your original xorg.conf.  Anyway, hope that helps.

Thanks for your input, do you happen to have any suggestions as to what I would do to "dive in", e.g. possible paths I may take to resolving this?

---

### Post by oneporter on 2008-07-25
I would go to [the website]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") mentioned in your first post and follow the instructions for Edgy 6.10, since that's the first one that doesn't start with "Use the Restricted Manager."  Let me know how it works out.

---

### Post by NvidiaN on 2008-07-25
> **oneporter said:**
> I would go to [the website]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") mentioned in your first post and follow the instructions for Edgy 6.10, since that's the first one that doesn't start with "Use the Restricted Manager."  Let me know how it works out.

tim@tim-laptop:~$ sudo apt-get install xorg-driver-fglrx
[sudo] password for tim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xorg-driver-fglrx is already the newest version.
The following packages were automatically installed and are no longer required:
  libglademm-2.4-1c2a
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tim@tim-laptop:~$ gksudo gedit /etc/default/linux-restricted-modules-common
tim@tim-laptop:~$ sudo aticonfig --initial
Data incomplete in file /etc/X11/xorg.conf
	[B]Device section "Configured Video Device" must have a Driver line.
aticonfig: Parsing the configuration file failed.[/B]
The above error messages are reported from XFree86 and may assist you in
diagnosing the problem with your configuration input file. Try use -f option
to generate a new configuration file.
tim@tim-laptop:~$ 

So I gave that a try, and I got stuck there, same place:

Section "Device"
Identifier "Configured Video Device"
EndSection

There's nothing in this section and there's apparently supposed to be. Thanks for the idea though, it sounded like a good one! Got any other ones?

---

### Post by oneporter on 2008-07-25
The page says to install *xorg-driver-fglrx* then *fglrx-control* then input the command *sudo depmod -a*, etc.. Were you looking in the [right place]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Instructions%20for%206.10%20(Edgy)")?

---

### Post by NvidiaN on 2008-07-25
> **oneporter said:**
> The page says to install *xorg-driver-fglrx* then *fglrx-control* then input the command *sudo depmod -a*, etc.. Were you looking in the [right place]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Instructions%20for%206.10%20(Edgy)")?

Yeah, I accidentally skipped the control step, I got past that part successfully. It's still giving me the: 

Data incomplete in file /etc/X11/xorg.conf
device section "Configured Video Device" must have a Driver line.
aticonfig: Parsing the configuration file failed.

error when I try to type *sudo aticonfig --initial* into the terminal. I don't know what the deal is. Is *sudo depmod -a* supposed to have any sort of effect when I type that, because it didn't. I just assumed it worked since I didn't get an error and went to the aticonfig step. :(

-e- and there's still nothing in the hardware drivers section.

---

### Post by oneporter on 2008-07-25
Have you tried restarting after depmod -a and then running the aticonfig --initial?  Depmod doesn't have any output it just tells the kernel that there's new stuff and it needs to configure itself accordingly.  Restarting after depmod -a is probably going to bork up your disply so I would go straight into recovery mode and tell aticonfig --initial to do it's buisness.  Possibly post your xorg.conf before you do that.  If you want to IM me I added my SN or use google chat with my e-mail addr [email]oneporter@gmail.com[/email], but I'm about to go to dinner so I might not be back around tonight.

---

### Post by NvidiaN on 2008-07-25
# xorg.conf (X.Org X Window System server configuration file)
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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by Rocket2DMn on 2008-07-25
OK, let's start over.  Uninstall the restricted drivers
```
sudo apt-get remove --purge xorg-driver-fglrx
```
If you used the Hardware Drivers program to install the drivers, remove them from there and PLEASE TELL ME that this was the case.  If you tried to install them with a downloaded file from ati's website, use that to remove the restricted drivers.

I am not able to pinpoint exactly how old your card is, but it seems to be from around 2003, which leads me to believe that it may not be supported by the restricted fglrx drivers, in which case we need to use the open source "ati" aka "radeon" drivers.

Now reconfigure X to get a generic xorg.conf file, which you seem to already have (but we'll do this step anyway)
```
sudo dpkg-reconfigure xserver-xorg -phigh
```

Since the open source drivers are used by default, restart your computer after removing the restricted drivers and running that last command.

Does the system boot up ok?  Are there any problems now?

---

### Post by NvidiaN on 2008-07-25
I uninstalled the drivers and ran the command, and followed that all with a restart. It's running okay in the sense that nothing exploded, but my graphics got worse, I think? Don't I not have drivers now?

And yes this card is from 2003, I got it when I graduated high school, haha. I thought however that it was supported (at least the 2d, I don't know what's going to be "optimal for me", I'll go with whatever you tell me): [http://xorg.freedesktop.org/releases/X11R6.7.0/doc/radeon.4.html](http://xorg.freedesktop.org/releases/X11R6.7.0/doc/radeon.4.html)

But in any case, I did what you asked, what next? P.s. thank you for your help!

---

### Post by Rocket2DMn on 2008-07-25
What do you mean by worse?  Do you not have full screen resolution?  Is what you should have available under System->Preferences->Screen Resolution?  If not, what is offered and what should be there?

When you go to System->Administration->Hardware Drivers, does it give you the option to install restricted drivers for your video card?

Please post your xorg.conf file
```
cat /etc/X11/xorg.conf
```

Since your card is not well supported, you may be stuck with mediocre graphics capabilities in Ubuntu, though we will try to get them as good as possible.

Also, please post
```
lsmod | grep radeon
```

---

### Post by NvidiaN on 2008-07-25
Well for instance scrolling down on a web page is choppy and fragmented, textures disappear (see attached images), and the start up screen loads like an old 56k full screen image...from the top down, and pretty slow. Also maximizing/minimizing windows is choppy. I'm sure there's more but that's all just off the top of my head!

```
tim@tim-laptop:~$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

```

...that file is still exactly the same as it was before (I posted it at the bottom of page one for someone else who was trying to help). Also:

```
radeon                124192  2 
drm                    82452  3 radeon
```


Thanks again for trying!

-e- the texture thing was occuring with default theme as well.
-e- and regarding going into the hardware driver manager, there is absolutely nothing in there and no option to install anything, just help/close.

---

### Post by Rocket2DMn on 2008-07-25
OK, everything else looks good.  First, you will probably never be able to use compiz (desktop effects) because of how old your card is.  Second, let's make sure xserver-xgl isn't installed
```
sudo apt-get remove --purge xserver-xgl
```
I'm not sure why scrolling is slow with compiz disabled, despite only having 2d acceleration.

Can you please post your /var/log/Xorg.0.log file for us?  It is probably better to attach this file rather than copying and pasting the content here.  Finally, please post the output of
```
sudo xresprobe radeon
```

If I can't pull any useful information from this, I'm rapidly running out of ideas.

---

### Post by NvidiaN on 2008-07-25
-The xserver xgl thing wasn't installed to begin with apparently.
-sudo xresprobe radeon came back with command not found.
-/var/log/Xorg.0.log is coming back with permission denied?

---

### Post by Rocket2DMn on 2008-07-25
OK, I guess that xresprobe isn't installed by default, I thought it was
```
sudo apt-get install xresprobe
```
Then try the command again.

Now we will copy that log file to a file in your home directory, set you as owner, then you can upload it here
```
sudo cp /var/log/Xorg.0.log ~/Xorg.0.log
sudo chown yourusername:yourusername ~/Xorg.0.log
```

---

### Post by NvidiaN on 2008-07-25
tim@tim-laptop:~$ sudo xresprobe radeon
id: 
res: 1024x768
freq: 
disptype: lcd/lvds

That showed up after a nifty screen flash.

I entered sudo cp /var/log/Xorg.0.log ~/Xorg.0.log
-nothing happened, entered sudo chown yourusername:yourusername ~/Xorg.0/log

but I'm not sure what my technical username is, is it tim, or tim@tim-laptop, or tim-laptop, and do I do like tim:tim or something else? I tried a bunch of combo's, none worked :/ I'm not very good at this lol.

---

### Post by Rocket2DMn on 2008-07-25
substitute "tim" for "yourusername".  tim-laptop is the computer name.

Is 1024x768 the normal resolution for your screen?

---

### Post by NvidiaN on 2008-07-25
chown: cannot access `/home/tim/Xorg.0/log': No such file or directory (weird, since I HAVE a home directory)

Yes 1024 is the normal resolution.

---

### Post by Rocket2DMn on 2008-07-25
Bah, I mistyped it, sorry.  I fixed my post above (it's a . not a /)

---

### Post by NvidiaN on 2008-07-25
It wouldn't let me attach a log file, and it said the openoffice file was too big so I'm doing this as code so it at least isn't too big, sorry!

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux tim-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 25 19:20:05 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1002,cab0 card 0000,0000 rev 13 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1002,700f card 0000,0000 rev 01 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 10b9,5237 card 103c,0024 rev 03 class 0c,03,10 hdr 00
(II) PCI: 00:06:0: chip 10b9,5451 card 103c,0024 rev 02 class 04,01,00 hdr 00
(II) PCI: 00:07:0: chip 10b9,1533 card 10b9,1533 rev 00 class 06,01,00 hdr 00
(II) PCI: 00:08:0: chip 10b9,5457 card 103c,0024 rev 00 class 07,03,00 hdr 00
(II) PCI: 00:09:0: chip 1260,3873 card 1468,0200 rev 01 class 02,80,00 hdr 00
(II) PCI: 00:0a:0: chip 1217,6972 card 1001,0000 rev 00 class 06,07,00 hdr 02
(II) PCI: 00:0c:0: chip 104c,8026 card 103c,0024 rev 00 class 0c,00,10 hdr 00
(II) PCI: 00:10:0: chip 10b9,5229 card 103c,0024 rev c4 class 01,01,b0 hdr 00
(II) PCI: 00:11:0: chip 10b9,7101 card 103c,0024 rev 00 class 06,80,00 hdr 00
(II) PCI: 00:12:0: chip 100b,0020 card 103c,0024 rev 00 class 02,00,00 hdr 00
(II) PCI: 01:05:0: chip 1002,4336 card 103c,0024 rev 00 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd0100000 - 0xd01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 2: bridge is at (0:10:0), (0,2,5), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[1] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x40000000 - 0x43ffffff (0x4000000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc Radeon Mobility U1 rev 0, Mem @ 0xe0000000/28, 0xd0100000/16, I/O @ 0x9000/8
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
(II) PCI Memory resource overlap reduced 0xd4000000 from 0xd7ffffff to 0xd3ffffff
(II) PCI Memory resource overlap reduced 0xd0400000 from 0xd0400fff to 0xd03fffff
(II) PCI I/O resource overlap reduced 0x00008090 from 0x00008093 to 0x0000808f
(II) Active PCI resource ranges:
	[0] -1	0	0xd0008000 - 0xd0008fff (0x1000) MX[B]
	[1] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[2] -1	0	0xd0007000 - 0xd00077ff (0x800) MX[B]
	[3] -1	0	0xd0401000 - 0xd0401fff (0x1000) MX[B]
	[4] -1	0	0xd0006000 - 0xd0006fff (0x1000) MX[B]
	[5] -1	0	0xd0005000 - 0xd0005fff (0x1000) MX[B]
	[6] -1	0	0xd0004000 - 0xd0004fff (0x1000) MX[B]
	[7] -1	0	0xd0400000 - 0xd03fffff (0x0) MX[B]O
	[8] -1	0	0xd4000000 - 0xd3ffffff (0x0) MX[B]O
	[9] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[11] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
	[12] -1	0	0x00008080 - 0x0000808f (0x10) IX[B]
	[13] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[14] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[15] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0x00008090 - 0x0000808f (0x0) IX[B]O
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd0008000 - 0xd0008fff (0x1000) MX[B]
	[1] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[2] -1	0	0xd0007000 - 0xd00077ff (0x800) MX[B]
	[3] -1	0	0xd0401000 - 0xd0401fff (0x1000) MX[B]
	[4] -1	0	0xd0006000 - 0xd0006fff (0x1000) MX[B]
	[5] -1	0	0xd0005000 - 0xd0005fff (0x1000) MX[B]
	[6] -1	0	0xd0004000 - 0xd0004fff (0x1000) MX[B]
	[7] -1	0	0xd0400000 - 0xd03fffff (0x0) MX[B]O
	[8] -1	0	0xd4000000 - 0xd3ffffff (0x0) MX[B]O
	[9] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[11] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
	[12] -1	0	0x00008080 - 0x0000808f (0x10) IX[B]
	[13] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[14] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[15] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x00008090 - 0x0000808f (0x0) IX[B]O
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
	[4] -1	0	0xd0008000 - 0xd0008fff (0x1000) MX[B]
	[5] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[6] -1	0	0xd0007000 - 0xd00077ff (0x800) MX[B]
	[7] -1	0	0xd0401000 - 0xd0401fff (0x1000) MX[B]
	[8] -1	0	0xd0006000 - 0xd0006fff (0x1000) MX[B]
	[9] -1	0	0xd0005000 - 0xd0005fff (0x1000) MX[B]
	[10] -1	0	0xd0004000 - 0xd0004fff (0x1000) MX[B]
	[11] -1	0	0xd0400000 - 0xd03fffff (0x0) MX[B]O
	[12] -1	0	0xd4000000 - 0xd3ffffff (0x0) MX[B]O
	[13] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
	[18] -1	0	0x00008080 - 0x0000808f (0x10) IX[B]
	[19] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[20] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[21] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[22] -1	0	0x00008090 - 0x0000808f (0x0) IX[B]O
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched ati from file name ati.ids in autoconfig
(==) Matched ati for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI Radeon X550XTX (RV370) 5657 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI  Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600, ATI RV610,
	ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
	ATI ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI RV610,
	ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI ATI RADEON E2400, ATI RV610,
	ATI RV670, ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI ATI Radeon HD 2600 XT AGP, ATI ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini ATI Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI ATI Radeon HD 2600 LE
(II) Primary Device is: PCI 01:05:0
(--) Assigning device section with no busID to primary device
(--) Chipset ATI Radeon IGP320M (U1) 4336 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0008000 - 0xd0008fff (0x1000) MX[B]
	[5] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[6] -1	0	0xd0007000 - 0xd00077ff (0x800) MX[B]
	[7] -1	0	0xd0401000 - 0xd0401fff (0x1000) MX[B]
	[8] -1	0	0xd0006000 - 0xd0006fff (0x1000) MX[B]
	[9] -1	0	0xd0005000 - 0xd0005fff (0x1000) MX[B]
	[10] -1	0	0xd0004000 - 0xd0004fff (0x1000) MX[B]
	[11] -1	0	0xd0400000 - 0xd03fffff (0x0) MX[B]O
	[12] -1	0	0xd4000000 - 0xd3ffffff (0x0) MX[B]O
	[13] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
	[18] -1	0	0x00008080 - 0x0000808f (0x10) IX[B]
	[19] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[20] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[21] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[22] -1	0	0x00008090 - 0x0000808f (0x0) IX[B]O
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0008000 - 0xd0008fff (0x1000) MX[B]
	[5] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[6] -1	0	0xd0007000 - 0xd00077ff (0x800) MX[B]
	[7] -1	0	0xd0401000 - 0xd0401fff (0x1000) MX[B]
	[8] -1	0	0xd0006000 - 0xd0006fff (0x1000) MX[B]
	[9] -1	0	0xd0005000 - 0xd0005fff (0x1000) MX[B]
	[10] -1	0	0xd0004000 - 0xd0004fff (0x1000) MX[B]
	[11] -1	0	0xd0400000 - 0xd03fffff (0x0) MX[B]O
	[12] -1	0	0xd4000000 - 0xd3ffffff (0x0) MX[B]O
	[13] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
	[21] -1	0	0x00008080 - 0x0000808f (0x10) IX[B]
	[22] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[23] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[24] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[25] -1	0	0x00008090 - 0x0000808f (0x0) IX[B]O
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0x00000000d0100000: size 64KB
(II) RADEON(0): PCI bus 1 card 5 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (==) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon IGP320M (U1) 4336" (ChipID = 0x4336)
(--) RADEON(0): Linear framebuffer at 0x00000000e0000000
(II) RADEON(0): AGP card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.28.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=65536K, accessible=131072K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 65536 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2048x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 19186, min_out_pll: 12000, max_out_pll: 35000, min_in_pll: 40, max_in_pll: 3000, xclk: 13300, sclk: 133.000000, mclk: 160.000000
(II) RADEON(0): PLL parameters: rf=19186 rd=426 min=12000 max=35000; xclk=13300
(WW) RADEON(0): LCD DDC Info Table found!
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-0x60, DACType-2, TMDSType-1, ConnectorType-1
(II) RADEON(0): Port4: DDCType-0x1a0, DACType-0, TMDSType-0, ConnectorType-7
(II) RADEON(0): Port5: DDCType-0x0, DACType-2, TMDSType-0, ConnectorType-5
(II) RADEON(0): Output VGA-0 using monitor section Configured Monitor
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output LVDS has no monitor section
(II) RADEON(0): Panel ID string: 1024x768                
(II) RADEON(0): Panel Size from BIOS: 1024x768
(II) RADEON(0): BIOS provided dividers will be used.
(WW) RADEON(0): LVDS Info:
XRes: 1024, YRes: 768, DotClock: 65000
HBlank: 320, HOverPlus: 16, HSyncWidth: 136
VBlank: 38, VOverPlus: 2, VSyncWidth: 6
(II) RADEON(0): I2C bus "LVDS" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: NTSC
(II) RADEON(0): TV standards supported by chip: NTSC PAL NTSC-J 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x60
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- LVDS
 DAC Type  -- None
 TMDS Type -- None
 DDC Type  -- 0x1a0
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
finished output detect: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output LVDS using initial mode 1024x768
after xf86InitialConfiguration
(==) RADEON(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0100000 - 0xd010ffff (0x10000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xd0008000 - 0xd0008fff (0x1000) MX[B]
	[7] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[8] -1	0	0xd0007000 - 0xd00077ff (0x800) MX[B]
	[9] -1	0	0xd0401000 - 0xd0401fff (0x1000) MX[B]
	[10] -1	0	0xd0006000 - 0xd0006fff (0x1000) MX[B]
	[11] -1	0	0xd0005000 - 0xd0005fff (0x1000) MX[B]
	[12] -1	0	0xd0004000 - 0xd0004fff (0x1000) MX[B]
	[13] -1	0	0xd0400000 - 0xd03fffff (0x0) MX[B]O
	[14] -1	0	0xd4000000 - 0xd3ffffff (0x0) MX[B]O
	[15] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[20] 0	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
	[24] -1	0	0x00008080 - 0x0000808f (0x10) IX[B]
	[25] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[26] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[27] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[28] -1	0	0x00008090 - 0x0000808f (0x0) IX[B]O
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit e0000000 0 0
(==) RADEON(0): Write-combining range (0xe0000000,0x4000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable montype: 2
(II) RADEON(0): Dynamic Clock Scaling Disabled
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x08000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1024,8191)
(II) RADEON(0): Reserved area from (0,1024) to (1024,1026)
(II) RADEON(0): Largest offscreen area available: 1024 x 7165
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x1000000
(II) RADEON(0): Will use depth buffer at offset 0x1400000
(II) RADEON(0): Will use 40960 kb for textures at offset 0x1800000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xe0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(==) RADEON(0): Using AGP 4x
(II) RADEON(0): [agp] Mode 0x0f000207 [AGP 0x1002/0xcab0; Card 0x1002/0x4336]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xd4000000
(II) RADEON(0): [agp] Ring mapped at 0xb795a000
(II) RADEON(0): [agp] ring read ptr handle = 0xd4101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb7959000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xd4102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xb3697000
(II) RADEON(0): [agp] GART texture map handle = 0xd4302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xb31b7000
(II) RADEON(0): [drm] register handle = 0xd0100000
(II) RADEON(0): [dri] Visual configs initialized
disable montype: 2
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3c00 0x3fff3c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
restore LVDS
enable montype: 2
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 2
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 10
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x3fff3c00 is: 0x3fff3c00
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xd47fd400
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3c00 0x3fff3c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xd47fd400
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Dashed Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor 0 (scanline 1026)
(II) RADEON(0): Using hardware cursor 1 (scanline 1030)
(II) RADEON(0): Largest offscreen area available: 1024 x 7157
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/radeon_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 270 x 203
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event8
(**) Option "Device" "/dev/input/event8"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event8
(**) Option "Device" "/dev/input/event8"
(--) Synaptics Touchpad touchpad found
enable montype: 2
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
SetClientVersion: 0 9
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) XAA: Evicting pixmaps
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
disable montype: 2
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3c00 0x3fff3c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xd47fd400
restore common
restore crtc1
restore pll1
restore LVDS
enable montype: 2
disable montype: 1
disable montype: 5
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
disable montype: 2
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3c00 0x3fff3c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xd47fd400
restore common
restore crtc1
restore pll1
restore LVDS
enable montype: 2
disable montype: 1
disable montype: 5
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) AIGLX: Suspending AIGLX clients for VT switch
disable montype: 2
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3c00 0x3fff3c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
finished PLL2
finished PLL1
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
disable montype: 2
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3c00 0x3fff3c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xd47fd400
restore common
restore crtc1
restore pll1
restore LVDS
enable montype: 2
(II) RADEON(0): [RESUME] Attempting to re-init Radeon hardware.
(==) RADEON(0): Using AGP 4x
(II) RADEON(0): [agp] Mode 0x0f000207 [AGP 0x1002/0xcab0; Card 0x1002/0x4336]
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x3fff3c00 is: 0x3fff3c00
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xd47fd400 is: 0xd47fd400
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3c00 0x3fff3c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xd47fd400
enable montype: 2
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event8
(**) Option "Device" "/dev/input/event8"
(--) Synaptics Touchpad touchpad found
```

---

### Post by Rocket2DMn on 2008-07-25
That's quite alright.

The log doesn't seem to tell us anything useful - there are no errors or anything else that immediately grabbed my attention.

I am basically out of ideas.  Just for kicks, I would like to see the output of these commands:
```
compiz --replace &
metacity --replace &
```

---

### Post by NvidiaN on 2008-07-25
Compiz:

```
Checking for Xgl: [1] 6505
tim@tim-laptop:~$ not present. 
Found laptop using ati driver. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

meta:

```
tim@tim-laptop:~$ Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered

```

Both flashed my screen, compiz put graphics settings on normal which made me laggier, meta seems to have put it back to none.

---

### Post by Rocket2DMn on 2008-07-25
That sounds like normal behavior to me, except I don't know where those errors are coming from with metacity (it's probably nothing).  Since I'm out of ideas, there are 2 things left to do, the first one is easy and should be done, the second is a bit more hassle and not necessary if you don't want to deal with it
1) make sure your system is up to date!
```
sudo apt-get update
sudo apt-get upgrade
```
2) file a bug report on Launchpad - [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)
If you choose to file a bug report about your problem, here are some directions and links to help out
-give a full explanation of your problem, and post a link to this thread.
-look at this page and be sure to attach the requested information to the bug report (as attachments!) - [uhelp]community/DebuggingXAutoconfiguration[/uhelp] (primarily look at step 5 under the Debug section).
-file the bug report under the package xserver-xorg-video-ati
-include info on what troubleshooting steps you have taken
-post screenshots as necessary
Finally, post a link on this thread to the bug report you filed.  All this will make for a very complete bug report.

---

### Post by NvidiaN on 2008-07-25
So you think I'm just S.O.L. and doomed to have sub-optimal graphics (comparing to what I had in windows) as long as I'm using this machine and am using linux?

That said, is it worth making a bug report? Is that going to help me in any way?

Whatever the case, thanks a ton for trying, it's good to know that I just can't have good graphics, and that it isn't just me not knowing how to get them set up properly. Thanks again.

---

### Post by Rocket2DMn on 2008-07-25
I can't say for sure what the future holds for you and your card.  It may just be your system, but filing a bug report can help in that future releases may have the card working flawlessly.  This at least presents the problem to developers.

---

### Post by ag65151 on 2008-07-26
I have another idea to see what is going on with your graphics. Please post the output of 

```
xrandr -q
```

---

### Post by NvidiaN on 2008-07-26
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 1024
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right x axis y axis)


In other news, currently reported as a bug: [https://bugs.launchpad.net/ubuntu/+bug/252138](https://bugs.launchpad.net/ubuntu/+bug/252138)

---

### Post by ag65151 on 2008-07-26
I asked for the xrandr output because I have had similar problems in the past. Sorry, it didn't give me any new ideas.

Do you happen to have compiz effects enabled (System -> Preferences -> Appearance -> [Visual Effects tab])? It should be set to none. I have had issues with those in the past also.

Sorry I can't be more help. Hope your bug gets some action.

---

### Post by oneporter on 2008-07-26
This may be a silly question, but are you using ubuntu server or desktop?  Also, do you have your files backed up / would you be willing to reinstall?

---

### Post by NvidiaN on 2008-07-26
> **ag65151 said:**
> I asked for the xrandr output because I have had similar problems in the past. Sorry, it didn't give me any new ideas.

Do you happen to have compiz effects enabled (System -> Preferences -> Appearance -> [Visual Effects tab])? It should be set to none. I have had issues with those in the past also.

Sorry I can't be more help. Hope your bug gets some action.

I do have it set to none, though the card should really be able to handle more based on my experience using it in windows...hell I could play world of warcraft in windows. I'm fine not playing it in linux, but I'd like to have SOME functionality here...you know?

Thanks for trying, I hope so too.

---

### Post by NvidiaN on 2008-07-26
> **oneporter said:**
> This may be a silly question, but are you using ubuntu server or desktop?  Also, do you have your files backed up / would you be willing to reinstall?

I am using desktop, lol. And I don't have anything backed up here (I'm at school), but I do have it all at home. So if I was sure reinstalling would fix my problem, I'd be more than willing to give it a go.

---

### Post by NvidiaN on 2008-08-25
Received an update about the bug via email asking me to try out an alpha to see if the bug was fixed.

Link to alpha: [http://cdimage.ubuntu.com/releases/intrepid/alpha-4/](http://cdimage.ubuntu.com/releases/intrepid/alpha-4/)

Does anyone happen to know whether or not there is anything special that must be done once the alpha is burned to a cd/I boot from said cd? Are there any special commands I should type to see whether the bug has been fixed, or should it just be immediately obvious based on the problems I've experienced?

---

