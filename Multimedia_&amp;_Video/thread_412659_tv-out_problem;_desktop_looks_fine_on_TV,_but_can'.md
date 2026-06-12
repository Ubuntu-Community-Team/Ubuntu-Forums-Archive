---
title: "tv-out problem; desktop looks fine on TV, but can't play movies"
date: 2007-04-18
forum: Multimedia &amp; Video
---

### Post by commonplace on 2007-04-18
Desktop computer with an ATI Radeon x700 (PCI-e) card. I just hooked up an s-video cable from the card to my TV. Took some fiddling with settings, but I got the output to work just fine. I can see my desktop both on my monitor (LCD) and my television. But, movies won't play on the TV.

My TV-out (s-video going to my TV) seems to work okay for everything except movie playback. What I mean is, I can see my desktop fine, I can surf the web fine, etc. It all looks great on the TV. But if I play a movie (a DVD, an AVI file, an MPG, whatever), it looks fine on my computer monitor but on the TV all that comes through is a blank blue screen (doesn't matter if it's full screen or windowed, wherever the movie would be, it's just blue -- if windowed, I still see the desktop and the video player (VLC, Mplayer, etc.) around it, but the actual movie display part is just blue.

Any ideas what could be wrong? I don't know a whole lot about this side of things (and I'm still fairly new to Linux), so... I don't know where to start. Doesn't seem like a problem in my xorg.conf because the output is fine for my normal desktop (even on the TV) but just movies won't play right. Thanks!

/Kevin

---

### Post by Gina on 2007-04-18
I have the same problem.  Same graphics card.  Actually, I get the problem with some Windows player apps too - forget which because  I don't use Windows much.

I too would like to know if anyone has an answer.

---

### Post by commonplace on 2007-04-18
> **Gina said:**
> I have the same problem.  Same graphics card.  Actually, I get the problem with some Windows player apps too - forget which because  I don't use Windows much.

Ugh. Well, at least it's not me or something I did wrong, I guess. Maybe future ATI drivers will resolve the problem. Or maybe it'll work in Feisty. Or... maybe I'll get an nVidia card someday.

If anyone else has any ideas or suggestions, I'd (we'd) love to hear 'em!

/Kevin

---

### Post by Gina on 2007-04-18
I'm planning to upgrade to Feisty on this PC shortly so will see.  Hoping I might be able to sort out TV card probs too.

---

### Post by commonplace on 2007-04-20
> **Gina said:**
> I'm planning to upgrade to Feisty on this PC shortly so will see.  Hoping I might be able to sort out TV card probs too.

Be sure to let us (me) know how it goes, especially if it helps with the TV-out problem! I'm going to Feisty soon, too.

/Kevin

---

### Post by Hasen_A on 2007-04-22
> **commonplace said:**
> My TV-out (s-video going to my TV) seems to work okay for everything except movie playback.

/Kevin

Would you please tell me your set up for /etc/X11/xorg.conf and which driver you are using? Can't get my S-Video output working for my X800.

---

### Post by commonplace on 2007-04-23
> **Hasen_A said:**
> Would you please tell me your set up for /etc/X11/xorg.conf and which driver you are using? Can't get my S-Video output working for my X800.

Sure! I've since switched to Feisty but this is the xorg.conf file as it was in Edgy:

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon X700 Pro (RV410)"
	Driver      "fglrx"
	Option	    "UseInternalAGPGART" "no"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "TVFormat" "NTSC-M"
	Option	    "TVOverscan" "on"
	BusID       "PCI:5:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon X700 Pro (RV410)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
```


For me, that got my display onto the TV screeen, at least. I couldn't play videos/movies, but at least I saw the desktop and it wasn't garbled or anything.

Now that I'm on Feisty, I'm using the opensource driver (which works great for my video card) and I haven't yet messed with the tvout yet. I might try to do that tonight. :)

/Kevin

---

### Post by flyingbrass on 2007-04-23
The open source driver doesn't do TV out.  Those of us with ATI cards wanting good S-video/composite TV output are screwed -- and have been for some time.

ATI's driver has had a problem with Xv TV output for many releases.  Xv is fine on the monitor.  it's only mangled when sent to the TV.  The bottom 1/3 or so is cut off.  ATI hasn't bothered to fix it.  X11 output, at least on my hardware, has a lot of tearing.  The "texturedvideo" now favored by ATI isn't much, if any, better.

If you want to see the picture on your monitor and TV at the same time, use X11.  One easy way is open the video in mplayer, choose preferences -> video, and set to X11 (XImage/Shm).  Stop and restart the video.

If you want it to fill the TV screen when the mplayer window on your monitor is in fullscreen mode (hit the f key for fullscreen), add zoom=yes to ~/.mplayer/config

If you want to see how messed up Xv TV out is, keep the video setting at Xv, pull up a terminal and do:

aticonfig --overlay-on=1

Don't worry about it complaining about not being able to write to xorg.conf.   The change still takes effect.  You'll get a black box on your desktop with the video showing on your TV.  To switch it back:

aticonfig --overlay-on=0

You can see a list of aticonfig options with: aticonfig --help

---

### Post by Hasen_A on 2007-04-24
> **flyingbrass said:**
> The open source driver doesn't do TV out.  Those of us with ATI cards wanting good S-video/composite TV output are screwed -- and have been for some time.


exactly which driver do I have to install to get TV-out working? I downloaded the driver from the ATI website and followed this [Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") for fglrx. My xorg.conf is displayed in a reply above. This is a repository (non-open source) driver right? fglrxinfo returns this:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GTO
OpenGL version string: 2.0.6458 (8.36.5)

```

---

### Post by flyingbrass on 2007-04-24
> **Hasen_A said:**
> exactly which driver do I have to install to get TV-out working?

The one you're using, fglrx.  

Try adding the line in red.

```
Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon X700 Pro (RV410)"
	Driver      "fglrx"
	Option	    "UseInternalAGPGART" "no"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "TVFormat" "NTSC-M"
[color=red]        Option      "TVStandard" "VIDEO"[/color]
	Option	    "TVOverscan" "on"
	BusID       "PCI:5:0:0"
EndSection
```

---

### Post by sloggerkhan on 2007-05-19
I've got on x700 and used both closed and open drivers. I seem to remember the key to video on TV out was making sure that video overlay was on the the s-vid screen.

---

### Post by Hasen_A on 2007-05-20
I got it working with the fglrx drivers using the SPM. Important: read out your PCI Bus using lspci and use the first address from your card.

---

### Post by peakshysteria on 2007-11-12
Any chance sloggerkhan and Hasen_A could tell us immortal n00bs how to accomplish the overlay and tv out with an ATI card. I didnt make it in my Gentoo...wich i'm now ditching for Ubuntu Gutsy Gibson this week. It would be nice with a step-by-step guide since tv out (with overlay) probably is something we all want. Without this we cant make a complete transition to Ubuntu. Would be nice to ditch XP for ever ;)

---

