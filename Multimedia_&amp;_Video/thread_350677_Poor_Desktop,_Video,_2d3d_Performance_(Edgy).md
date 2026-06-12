---
title: "Poor Desktop, Video, 2d/3d Performance (Edgy)"
date: 2007-01-31
forum: Multimedia &amp; Video
---

### Post by mirzmaster on 2007-01-31
I've been meaning to post on these forums asking for some help with my desktop performance on Edgy.  As a media buff, I just haven't been able to get the desktop/video performance out of my Ubuntu experience that I was looking for.

Video playback is fine at normal resolutions, but my system starts choking when playing 720p video (uses 100% CPU).  This makes it downright impossible to do **anything** else while watching high-def video.  Likewise, 3d acceleration seems to be nearly non-functioning.  Even a game with graphics as straightforward as Geometry Wars suffers.

**[COLOR="Red"]If I had to summarize my problem I'd say that it appears like all graphics are being rendered by the CPU.  Hardware acceleration doesn't seem to function at all.[/COLOR]**

All this is being done on an Athlon 3200+, 1GB memory, ATI 8600 Pro (256MB).  On the same hardware configuration I could play 720p video with ease, whilst performing other tasks (browsing, etc.), which I find impossible on Ubuntu.

I should also mention the following relevant points:

[LIST]
[*]I'm running the fglrx driver.
[*]I've managed to get Beryl running before, but it too felt like it was running with hardware-acceleration disabled (all effects seriously spiked CPU usage, and were very slow).  It did not feel smoothly-accelerated as I've experienced before with the Koraraa XGL Live CD.
[*]720p video, even without any other apps running, suffers from dropped frames, loss of audio sync, etc.
[*]I've followed nearly every fglrx and Ubuntu video guide I've come across, without success.
[*]I have played around with xorg.conf plenty.  I've tried a ridiculous number of permutations of the Device Options to no avail.
[/LIST]

The following is the output of fglrxinfo:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6011 (8.28.8)
```

Here is the Device section of xorg.conf:

```
Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
	Option	"XaaNoOffscreenPixmaps"
#	Option	"AccelMethod" "EXA"
	Option	"AGPMode" "8"
	Option	"AGPFastWrite" "yes"
	Option	"EnablePageFlip" "on"
	Option	"ColorTiling"	"on"
	Option	"RenderAccel" "yes"
	Option	"mtrr" "off"
	Option	"UseInternalAGPGART" "no"
	Option	"UseFastTLS" "1"
	BusID	"AGP:1:0:0"
EndSection
```

The result of:
```
cat /var/log/Xorg.0.log | grep "EE"
```

is:

```
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
```

I believe the AIGLX error only recently started appearing, though I could be mistaken.

Any kind soul out there have any clue what the problem could be and how I should go about correcting it?  :)

Thank you, Ubuntu Community!

---

### Post by mirzmaster on 2007-02-01
Nada, eh?

If there are no suggestions then I will likely think about restarting my desktop configuration, and attempting to go with the free "ati" driver and AIGLX.  Is there any reason to believe this might take care of my problem?

How would I go about rebuilding my display settings anyway?  Would I need to employ dpkg-reconfigure like so??? :

```
sudo dpkg-reconfigure gdm
```

---

### Post by Patrick-Ruff on 2007-02-01
ATI 6800? you've got to be kidding me . . . that's like the oldest ATI card I've ever heard of. (with the exception of 3d rage)

---

### Post by mirzmaster on 2007-02-02
Woah, big mistake.  That should be ATI 8600 Pro (256MB)!  :)

---

