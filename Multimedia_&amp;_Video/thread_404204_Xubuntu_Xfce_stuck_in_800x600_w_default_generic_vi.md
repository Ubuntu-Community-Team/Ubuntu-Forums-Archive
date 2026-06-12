---
title: "Xubuntu Xfce stuck in 800x600 w/ default generic video driver?"
date: 2007-04-08
forum: Multimedia &amp; Video
---

### Post by SubGothius on 2007-04-08
[I recently installed Xubuntu 6.10 Edgy](http://ubuntuforums.org/showthread.php?t=395441) on an old machine with an old ixMicro/IMS TwinTurbo 128+ PCI video card.

After installation, my new Xubuntu boots into a 800x600 resolution that's shrunken and squeezed off the left side of the screen, appearing the same as when I select 800x600 in my other OS (obviously not a well-supported vmode for this monitor+card!), and I can't select anything but 800x600 and 640x480 in the Xfce Display settings panel (even tho' I specified 1024x768 in the Installer as the only valid rez for X), so I think it's defaulting to a generic video driver and resolution instead of the imsttfb driver. I am specifying the kernel argument "video=imsttfb:vmode:17,cmode:32" (also tried substituting "vmode:16", "cmode:24", or adding ",mclk:75" to the end) in my bootloader, to no avail; perhaps this is not the right karg, or maybe I need to edit my xorg.conf ... :confused:

Also FWIW, after running all available Updates and customizing some Xfce panels and windowing options, now I can't seem to launch any applications from the Applications menu.  Whenever I try, my drive chatters briefly like it's going to do something, but then nothing happens.  Only Xfce utilities like the Settings Manager and Process Manager will open, and the Process Manager doesn't list any new processes when I try to launch an app. ([Please respond to this secondary issue in its own dedicated thread - click here](http://ubuntuforums.org/showthread.php?t=404196).)

---

### Post by kerry_s on 2007-04-08
Have you run->
sudo dpkg-reconfigure -phigh xserver-xorg

For the not launching try rebooting, it may have updated some applications that aren't set yet.

---

### Post by SubGothius on 2007-04-08
In an earlier install attempt, I had tried building a new xorg.conf with what you suggest (absent your -phigh flags in that case however), which did not seem to fix the driver/resolution issue, even tho' the new xorg.conf appeared to have my correct driver name, preferred resolution(s), etc., and moreover seemed to risk doing odd things to my input peripheral behaviour depending on how I handled those stages of the reconfigure routine.  Granted, I ran out of space on "/" that time, so maybe that's why it didn't take.  Can't I just reconfigure the video params without altering the input params as well (tho' I'll have to see if your flags will accomplish that)?

(Other issue re: app-launching continued in its own thread. ;) )

---

### Post by pxwpxw on 2007-04-08
oldworldmac, bootx and xorg.conf

My notes (2006) from pmac7300 for xorg.conf.
(Onboard Apple video).

I finally used fbdev.
I also had to add a Modeline to suit a LCD monitor, and check the Hsync and Vrefresh figures.

From notes, roughly as follows, refer xorg.conf for correct terms.


In Macos bootx config - allow video driver.
Macos video resolution and colour setting may have influence when running Bootx.

In xorg.conf fbdev demands inclusion of default depth 15, and
the first display subsection must be depth 8.
Does not necessarilu use these.

See man fbdev re screen display modes.

Section "Device"
	----
	Driver "fbdev"
	Option "UseFBDev" "true"
	----
EndSection

In Section "Screen"
##has to include  .....
DefaultDepth 15
## first subsection Display has to be depth 8
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768"
EndSubSection
-----

---

### Post by RedSquirrel on 2007-04-08
> **SubGothius said:**
> In an earlier install attempt, I had tried building a new xorg.conf with what you suggest (absent your -phigh flags in that case however), which did not seem to fix the driver/resolution issue, even tho' the new xorg.conf appeared to have my correct driver name, preferred resolution(s), etc., and moreover seemed to risk doing odd things to my input peripheral behaviour depending on how I handled those stages of the reconfigure routine.  Granted, I ran out of space on "/" that time, so maybe that's why it didn't take.  Can't I just reconfigure the video params without altering the input params as well (tho' I'll have to see if your flags will accomplish that)?



You can edit /etc/X11/xorg.conf directly. Make a backup copy first, though, just in case you make a mistake or your new settings are even worse. :)

[This guide]("http://ubuntuforums.org/showthread.php?p=454217") is helpful.

---

### Post by SubGothius on 2007-04-09
When I run "lspci -x" it says my video card is at 00:0e.0 on the PCI bus-- so this should be equivalent to PCI:0:14:0 in my xorg.conf, yes?  X now refuses to start with this setting, saying it can't find the expected device at PCI:0:14:0 ... :confused:

---

### Post by pxwpxw on 2007-04-09
Try omittting BusId from xorg.conf if you havbe only one card (man xorg.conf says so)

---

### Post by SubGothius on 2007-04-15
FYI, I finally fixed this by simply editing my xorg.conf -- the HorizSync and VertRefresh values in my xorg.conf Monitor section were both waaay too low, so apparently the 800x600 I was getting was the only rez I could get within those low rate ranges.  Updated HorizSync to 31-61, and VertRefresh to 60-75, and now all is well...

...that is, aside from the fact that [my red and blue channels appear to be swapped somehow](http://ubuntuforums.org/showthread.php?t=410001)!?

---

### Post by Tommy on 2007-05-18
I know this isn't exactly helpful, but I have an IMS Twin Turbo card (gigantic thing that comes with a Power Mac 9600) and eventually I gave up and bought a known well-supported video card from someone on eBay. I think it's for a "Blue & White" G3. I have never had trouble with video working on that card... though I apologize I don't know which card it is right now. 

As I said, I know it's not exactly helpful, but that IMS card is absolutely frustrating, and even though I wanted to get things going with the "stock" arrangement I gave up on that card a long time ago.

Actually as time has gone on I have had so much trouble getting Ubuntu going at all on the PowerMac 9600 that I have set it aside for several months. Haven't tried Feisty yet but your threads are inspiring me to try again. Thank you!

---

### Post by SubGothius on 2007-05-18
Thanks, but I *did* finally get the IMS card working properly.  I had to make a couple *very* simple edits in my /etc/X11/xorg.conf to make sure the Horizontal Sync and Vertical Refresh values matched my monitor specs (the default values were *waaay* too low for any modern CRT monitor), and add a line which (I *think*?) tells the card to process video in 32-bit color but output as 24-bit color (or maybe it's a pure hack: dunno how or why it works, but it does ;) ); here's the relevant sections of my xorg.conf, with my edits pointed out by a #NOTE comment:```
Section "Device"
	Identifier	"Integrated Micro Solutions Inc. IMS9128 [Twin turbo 128]"
	Driver		"imstt"
	Option		"UseFBDev"		"false"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-61          #NOTE updated values
	VertRefresh	60-75          #NOTE updated values
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Integrated Micro Solutions Inc. IMS9128 [Twin turbo 128]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	DefaultFbBpp	32          #NOTE imsttfb hack
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```
Due to the disk-detection issues I encountered with Feisty, and with Ubuntu having dropped official support for our PowerPC platform, I am strongly inclined to go back to Edgy, or possibly even try the new Debian v4.0 "Etch", which will officially support our PowerPC platform for the foreseeable future.  I had successfully [netboot installed Debian v3.1 "Sarge"](http://ftp.debian.org/dists/sarge/main/installer-powerpc/current/images/powerpc/netboot/) before quickly running out of space post-install on the too-skimpy / partition I'd made, and then realized I could apply the lessons learned there towards [my method  for installing Xubuntu v6.10 Edgy on an OldWorld PPC Mac](http://ubuntuforums.org/showthread.php?p=2419715#post2419715).

Also favoring Debian Etch (too bad they only [seem to] offer CD ISOs for Etch now, rather than just a straight D/L of a kernel and initrd.gz netboot installer that BootX can use directly, as Sarge offered [FOUND: See below]), I kinda dig the idea of possibly ditching (or having an alternative to) the Xfce4/Xubuntu-Desktop in favor of the even-snappier GNUstep environment (or at least WindowMaker+GWorkspace.app as a NeXT-clone Desktop), and I suspect that might tend to work out better with a "proper" Debian than it would with Ubuntu.  Besides, since Ubuntu's primary benefits vs. Debian seem kinda moot for an OldWorld Mac (Ease of install? Not so much. Hardware detection/support? Debian's was better. *Maybe* ready-made suites of Desktop software apps, but I can use Synaptic just as well in Debian to find all the packages I'd want, and then "aptitude install" them for better dependency handling...)

The only reason I have tacked all this is because I can't afford any new gear whatsoever (even $20 for a 128MB  RAM upgrade is a stretch for my current budget!), and MacOS 9 is starting to get tired (e.g., the most modern, capable browser available for Mac OS 9 is [WaMCom, a variant of Mozilla v1.3.1 from 2003](http://wamcom.org/)), so I have little choice but to try to "run what I brung" for free on Linux. Since Debian still officially supports "Old World" PPC and Ubuntu is based on Debian, that's how I wound up here. ;)

Good luck in your own quest! 8)

---

### Post by pxwpxw on 2007-05-20
**SubGothius**

> Debian Etch (too bad they only offer CD ISOs for Etch now, rather than just a straight D/L of a kernel and initrd.gz netboot installer that BootX can use directly, as Sarge offered),

Did you look here? (stable is Etch now)

[http://www.us.debian.org/releases/stable/powerpc/ch04s02.html.en](http://www.us.debian.org/releases/stable/powerpc/ch04s02.html.en)

[http://www.us.debian.org/CD/](http://www.us.debian.org/CD/)

---

### Post by SubGothius on 2007-05-20
Thanks!  I had not found that first archive you mention, was searching thru ftp.debian.org instead. Mad Mac props to pxwpxw! :lol:

[Debian 4.0 Etch netboot-installer 'vmlinux' kernel and 'initrd.gz' files suitable for OldWorld PowerMacs are here](http://http.us.debian.org/debian/dists/etch/main/installer-powerpc/current//images/powerpc/netboot/) (D/L into Mac OS 7/8/9 for use by [BootX](http://penguinppc.org/bootloaders/bootx/) directly) -- for non-US D/L mirrors, see links in pxwpxw's post above.

[Debian 4.0 Etch CD image ISO files suitable for OldWorld PowerMacs are here](http://cdimage.debian.org/debian-cd/4.0_r0/powerpc/iso-cd/) (only Disc 1 is necessary for a normal Desktop install, variants at the end of the list available for KDE or Xfce desktops, minimal-install, or a smaller "businesscard" ISO that D/Ls quickly and performs a netboot install) -- also see links in pxwpxw's post above to find other (better if you can use them) D/L methods and mirror sites.

---

