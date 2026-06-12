---
title: "xrandr + s-video + ATIradeon9100 = garbled output"
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by se2131 on 2007-12-01
I'm trying to get s-video working on my laptop, which has an ATI Radeon 9100 card. After switching to the "radeon" driver, I typed in the following commands:

```

xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600

```

I get output on the TV, but it's all garbled (I can vaguely see my desktop on the TV, but it's scrambled). Any ideas on what I should try?

---

### Post by se2131 on 2007-12-01
Btw, this is not an HDTV, xrandr doesn't let me add any modes besides 800x600, and the TV is NTSC.

Here's the xrandr --verbose output

```

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 800
VGA-0 disconnected (normal left inverted right)
        Identifier: 0x4c
        Timestamp:  -1751197830
        Subpixel:   no subpixels
        Clones:    
        CRTCs:      0 1
        load_detection: 0 (0x00000000) range:  (0,1)
LVDS connected 1280x800+0+0 (0x4f) normal (normal left inverted right) 0mm x 0mm
        Identifier: 0x4d
        Timestamp:  -1751197830
        Subpixel:   horizontal rgb
        Clones:    
        CRTC:       0
        CRTCs:      0
                scaler: full
        backlight: 255 (0x000000ff) range:  (0,255)
  1280x800 (0x4f)   71.2MHz
        h: width  1280 start 1328 end 1352 total 1440 skew    0 clock   49.5KHz
        v: height  800 start  802 end  808 total  823           clock   60.1Hz
  1280x800 (0x50)   83.5MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   49.7KHz
        v: height  800 start  801 end  804 total  828           clock   60.0Hz
  1280x768 (0x51)   80.1MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   47.7KHz
        v: height  768 start  769 end  772 total  795           clock   60.0Hz
  1024x768 (0x52)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x53)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x54)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
  640x480 (0x55)   23.8MHz -HSync +VSync
        h: width   640 start  664 end  720 total  800 skew    0 clock   29.7KHz
        v: height  480 start  483 end  487 total  500           clock   59.4Hz
S-video disconnected 800x600+0+0 (0x53) normal (normal left inverted right) 0mm x 0mm
        Identifier: 0x4e
        Timestamp:  -1751197830
        Subpixel:   no subpixels
        Clones:    
        CRTC:       1
        CRTCs:      0 1
                tv_standard: ntsc-j
        tv_vertical_position: 0 (0x00000000) range:  (-5,5)
        tv_horizontal_position: 0 (0x00000000) range:  (-5,5)
        tv_horizontal_size: 0 (0x00000000) range:  (-5,5)
        load_detection: 0 (0x00000000) range:  (0,1)
  800x600 (0x53)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz

```

---

### Post by se2131 on 2007-12-03
bump, anyone?

---

### Post by se2131 on 2007-12-08
another bump, this is the only thing preventing me from getting rid of dual-boot windows

---

### Post by se2131 on 2008-03-19
Bumping again after updating to Hardy Heron Alpha and not seeing any difference (was hoping the new XOrg would change something)

---

### Post by g_dwarf on 2008-04-01
I have the same problem but with PAL tv, will let you know when I find a solution

---

### Post by aeiah on 2008-04-01
is there a reason why you have chosen NTSC-J instead of NTSC? is NTSC-J japanese? there may also be an NTSC-M option, although im not sure

edit: seems there are these:

NTSC-M
NTSC-N
NTSC-JPN
PAL-B
PAL-D
PAL-G
PAL-H
PAL-I
PAL-K
PAL-L
PAL-N
PAL-M
PAL-SCART
PAL-CN
PAL-K1

and according to this page here: [http://www.linuxquestions.org/questions/susenovell-60/ati-and-linux-is-so-easy-356511/?highlight=ATI+Radeon+xpress+200M](http://www.linuxquestions.org/questions/susenovell-60/ati-and-linux-is-so-easy-356511/?highlight=ATI+Radeon+xpress+200M) it may not support above 24bit colour depth (although i know this is a different ati card)

---

### Post by g_dwarf on 2008-04-01
I don't think that's the problem, mine is set to pal, I tried:
```

$ xrandr --output S-video --set tv_standard pal-b
$ xrandr --output S-video --set tv_standard palb

```
but it doesn't recognize anything other than pal (or ntsc).

Or is this something I should set in xorg.conf? In the Device-section I have now:
```

	Option		"ForceTVOut"	"true"
	Option		"TVStandard"	"pal"

```

xrandr -q:
```

S-video connected 800x600+0+0 (0x4f) normal (normal left inverted right x axis y axis) 0mm x 0mm
	Identifier: 0x46
	Timestamp:  28512
	Subpixel:   no subpixels
	Clones:    
	CRTC:       1
	CRTCs:      0 1
		tv_standard: pal
	tv_vertical_position: 0 (0x00000000) range:  (-5,5)
	tv_horizontal_position: 0 (0x00000000) range:  (-5,5)
	tv_horizontal_size: 0 (0x00000000) range:  (-5,5)
	load_detection: 0 (0x00000000) range:  (0,1)
  800x600 (0x4f)   38.2MHz -HSync +VSync
        h: width   800 start  832 end  912 total 1024 skew    0 clock   37.4KHz
        v: height  600 start  603 end  607 total  624           clock   59.9Hz
  800x600 (0x4c)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz

```

I have a Radeon Xpress 1100.

---

### Post by g_dwarf on 2008-04-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/xorg-server/+bug/161893](https://bugs.launchpad.net/xorg-server/+bug/161893) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Well I've had no luck so far. I found a number of sources that seemed to be maybe helpful, allthough they are about different cards it seems to be the same problem.

[Link: Bugreport for same problem on ATI Radeon 9200]("http://bugs.freedesktop.org/show_bug.cgi?id=12007#c0") on freedesktop.org.
The last comment by Alex Deucher suggests there's no solution yet.
([Link: The same bug in Ubuntu Launchpad]("https://bugs.launchpad.net/xorg-server/+bug/161893"))

[Link: Bugreport for same problem on ATI Radeon Xpress 200M]("http://www.mail-archive.com/debian-x@lists.debian.org/msg71667.html") suggests that setting VGA-0 to Ignore in xorg.conf may help, since only two crtc's can be used simultaneously.

This led me to discover (after a long time) that Option "Ignore" "true" doesn't work, instead one should use [Option "Disable" "true" (link)]("http://www.mail-archive.com/debian-x@lists.debian.org/msg74545.html")  - otherwise X.Org will not load altogether. Eventually this didn't help either, though, VGA-0 Disabled / Ignored or not, the static stays the same.

---

