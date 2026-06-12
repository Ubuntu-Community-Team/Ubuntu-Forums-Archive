---
title: "ati radeon driver: dualhead and XV, changing overlay"
date: 2007-09-19
forum: Multimedia &amp; Video
---

### Post by segalion on 2007-09-19
Anybody know how to change XV overlay between two display in a xinerama config with radeon driver?

With fglrx, you can do somethig like: 
>sudo aticonfig -ovon=[0|1]

Are there somethig similar in X radeon driver?
If not, how you can set XV overlay statically in xorg.conf.
Seems that you can do this with "option overlayonCRT2" in mergedfb config, but nothing similar in xinerama...

Thanks in advance...

My xorg.config:
```

...

Section "Device"
	Identifier	"0 ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Driver		"ati"
	Option		"MonitorLayout" "LVDS,CRT"	
	Option		"DDCMode" "True"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"1 ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Driver		"ati"
	Option		"MonitorLayout" "LVDS,CRT"	
	Option		"DDCMode" "True"	
	BusID		"PCI:1:0:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Main Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier   "Second Monitor"
	HorizSync    14.0 - 16.0
	VertRefresh  50.0 - 50.0
	Option      "DPMS"
	Modeline "720x540" 15.101 720 778 850 968 540 561 566 624 +HSync +Vsync Interlace Composite
EndSection 

Section "Screen"
	Identifier	"Main Screen"
	Device		"0 ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Main Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "720x540"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Device		"1 ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Second Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth     24
		Modes    "720x540"
	EndSubSection 
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Main Screen"
	Screen		1 "Second Screen" Relative "Main Screen" 0 1
	Option		"Xinerama" "true"
...
EndSection
...

```

---

### Post by segalion on 2007-10-23
Solved in [http://ubuntuforums.org/showthread.php?p=3467287#post3467287](http://ubuntuforums.org/showthread.php?p=3467287#post3467287)

xvattr -a XV_CRTC -v 1

---

### Post by CarpKing on 2007-10-26
Any way to make the overlay go fullscreen on the smaller display?

---

### Post by segalion on 2007-11-12
> **CarpKing said:**
> Any way to make the overlay go fullscreen on the smaller display?

No.
Only making fullscreen from application. I use gxine with fullscreen autostart.

---

### Post by CarpKing on 2007-11-12
> **segalion said:**
> No.
Only making fullscreen from application. I use gxine with fullscreen autostart.

Hmm... That's really kind of what I meant.  But can it go fullscreen *just* on the smaller display?  When I try to go fullscreen it goes to the size of my main monitor, so only part of the video is visible on the TV.

---

### Post by segalion on 2007-11-13
Ok, maybe you could change the big desktop to low resolution before making fullscreen.
I.e. in my computer 
```
xrandr -s 4

```force screen to 1024x768
and 
```
xrandr -s 0
```
return to 1440x900

Now, I´m using the new fglxr driver, that has corrected the XV tv-out, and I use aticonfig to redirect XV, and I have two scripts to change resolution and overlay monitor:

tv_on.sh 
```
xrandr -s 4
aticonfig --enable-monitor=lvds,tv --ovon=1 --tv-overscan=off --tv-geometry=30x100+6+1 --nobackup

```

tv-off.sh
```
xrandr -s 0
aticonfig --ovon=0 --nobackup

```

Then, I have my .lircrc config to switch between then with my remote control:
```

[...]
begin
        prog = irexec
        button = DVD_Ok
        config = $HOME/tv_on.sh
        config = $HOME/tv_off.sh
end
[...]
begin
         button = DVD_Return
         prog   = gxine
         config = vdr ('1') || play (10, 0);
         config = vdr ('2') || play (20, 0);
         config = vdr ('3') || play (30, 0);
         config = vdr ('4') || play (40, 0);
         config = vdr ('5') || play (50, 0);
         config = vdr ('6') || play (60, 0);
         config = vdr ('7') || play (70, 0);
         config = vdr ('8') || play (80, 0);
         config = vdr ('9') || play (90, 0);
         config = vdr ('0') || play (0, 0);
end
# cycle aspect ratio values
begin
         button = DVD_Setup
         prog   = gxine
         config = ++vo_aspect.v;
end
# fullscreen toggle
begin
         button = DVD_Digits
         prog   = gxine
         config = vo_fullscreen.toggle ();
end
[...]
```

The change between modes works fine even with gxine playing video.

---

### Post by CarpKing on 2007-11-28
I figured out how to do generally what I wanted: [http://ubuntuforums.org/showthread.php?p=3854367](http://ubuntuforums.org/showthread.php?p=3854367)

---

