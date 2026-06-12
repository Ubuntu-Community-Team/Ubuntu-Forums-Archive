---
title: "help with multiple X sessions on multiple monitors"
date: 2008-10-13
forum: Multimedia Software
---

### Post by jivanyatra on 2008-10-13
Hi all!

I've been browsing these amazing forums for some time now with regards to my problem.  A little background: I'm running hardy on a computer with an ATI Radeon 9200 Pro, and I'm using the open source "ati" driver, as it is unsupported by the proprietary one.  I have a CRT attached with 1152x864 resolution.

Essentially, I'd like to setup the S-video out to my TV, and run a separate X server specifically for the TV, so I can play videos (both locally and streaming), slideshows, etc., possibly even a whole second gnome session.

I've tried over and over to reconfigure my xorg.conf file, and had a stretched desktop setup working, but it would continually glitch out and display messed up graphics, VNC would have problems, etc.  I've tried Xrandr, and while versatile, it was ultimately unsuccessful for my purposes.  Because of it though, I've learned that I also have to include a "ForceTVOut" option in my xorg.conf to get my computer to recognize the S-video connection to my TV.

I've decided that trying separate X sessions is probably better in the long-run, and I could connect to the other session via VNC as well to control things for my tv remotely.  I've scoured the web for instructions on getting two X sessions running simultaneously on two separate monitors (with separate resolutions), but I've turned up nothing.

Any and all help is appreciated greatly!  It's my first post to the forums, and while I've been silent for many months, I hope to change that!

---

### Post by jivanyatra on 2008-10-22
After much tinkering, I've found out that despite it being recognized as a 9200 pro, it's actually a 9250.  Both series of cards have horrible support...

Fglrx doesn't support this card anymore, and I can't install the older drivers from the website, as I get an error: 

```
Architecture: i686 (32-bit)
X Server: unable to detect
Removing temporary directory: fglrx-install

```

I've resorted to cloning the monitor, at 800x600 (ugh) and since I don't use the computer incredibly often, I suppose I can make do.  However, I have another problem.

The ouput on my TV from S-video is not aligned properly.  there's about a 20 pixel section cutoff from the top of the tv, and there's a 20 pixel section of black on the bottom of the tv.  Same thing with the left and right sides of the tv.

Using xrandr, i do
```
xrandr --output S-video --pos -10x-20
```

What this does is it messes up the screen (on both the monitor and TV of course) and the display on the tv is still cut off.

However, in Windows, it aligns perfectly, no issues.  Since I'm using the open-source driver, I can't use the catalyst system or anything of the like to realign everything properly.  Anyone have any ideas?

---

### Post by jivanyatra on 2008-10-22
Sorry for another post..

As an alternative, I've also included below my xorg.conf file.  This gives me a spanned desktop, with the S-video alignment problem (as outlined in post #2).  I'd be fine with two separate X sessions, but this doesn't give it to me.

```


Section "Device"
	Identifier	"Radeon 9200"  #"Configured Video Device"
	Driver		"ati"
	Option		"ForceTVOut" "on"
	Option		"TVOutFormat" "SVIDEO"
#	Option		"TVStandard" "ntsc"
	Option    	"monitor-VGA-0" "CRT"
	Option    	"monitor-S-video" "TV"
	BusID		"PCI:2:6:0"
	Screen 		0
EndSection

Section "Device"
	Identifier	"Radeon 9200 2"
	Driver		"ati"
	Option		"ForceTVOut" "on"
	Option		"TVStandard" "ntsc"
	Option		"monitor-VGA-0" "CRT"
	Option		"monitor-S-video" "TV"
	BusID		"PCI:2:6:0"
##	BusID		"PCI:2:6:1"  ## This doesn't work.
	Screen 		1
EndSection		

Section "Monitor"
	Identifier	"CRT"
EndSection

Section "Monitor"
	Identifier	"TV"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"CRT"
	Device		"Radeon 9200"
	SubSection "Display"
		Depth 24
		Modes "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600"
#		Virtual 1952 864
	EndSubSection
EndSection

Section "Screen"
	Identifier	"TV Screen"
	Monitor		"TV"
	Device		"Radeon 9200 2"
	SubSection "Display"
		Depth 24
		Modes "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Default Screen" 0 0
	Screen 1	"TV Screen" RightOf "Default Screen"
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection
```

In addition, all of the problem occur whether or not Compiz is enabled.

---

