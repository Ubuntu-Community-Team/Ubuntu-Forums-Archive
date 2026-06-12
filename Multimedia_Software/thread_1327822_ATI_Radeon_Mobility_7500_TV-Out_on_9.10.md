---
title: "ATI Radeon Mobility 7500 TV-Out on 9.10"
date: 2009-11-15
forum: Multimedia Software
---

### Post by jakj on 2009-11-15
I've tried every atitvout and xrandr solution I could find on the entire Internet, and my TV-out works in XP but not Ubuntu. I haven't tried 3D-rendering or fullscreen video yet, but simple 2D desktop stuff works fine so far.

Box: Dell Latitude C640

Video: 01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

OS: Ubuntu 9.10 32-bit

(All hardware works fine in Windows XP -- Already checked it that way.)

Using xserver-xorg-video-radeon driver that came with the installation. Installed atitvout package to go with it.

$ sudo atitvout detect
CRT is attached.
TV is attached via S-Video.
$ sudo atitvout t
VBE call failed.
Maybe this command is not supported by your graphics adapter?
Did your parameters (if you specified some) really make sense?
Please try all other available commands before complaining!

$ xrandr --verbose
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 (0x102) normal (normal) 0mm x 0mm
    Identifier: 0x101
    Timestamp:  34877
    Subpixel:   unknown
    Clones:    
    CRTC:       0
    CRTCs:      0
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
  1024x768 (0x102)    0.0MHz *current
        h: width  1024 start    0 end    0 total 1024 skew    0 clock    0.0KHz
        v: height  768 start    0 end    0 total  768           clock    0.0Hz
  800x600 (0x103)   29.3MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   36.6KHz
        v: height  600 start    0 end    0 total  600           clock   61.0Hz

$ xrandr --output S-video --set load_detection 1
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  19
  Current serial number in output stream:  19

$ cat /etc/X11/xorg.conf
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

### Post by jakj on 2009-11-19
Anyone had any luck with this machine on this issue?

I've tried editing my xorg.conf to use driver "radeon" instead of "vesa", but it never works. Half the time I get a black screen with two white bars on the top and bottom (looks like it gets stuck after it draws the backgrounds of the trays?), and half the time it's on the burgundy-ish Ubuntu loading screen with the progress bar and just sticks and doesn't come out. I have to hard-reset the machine and get into recovery mode to restore the xorg.conf to get it to come up again.

---

### Post by Thelasko on 2009-11-25
try using ```
sudo atitvout -f t
```
or
```
sudo atitvout -r t
```

---

### Post by sedstevo on 2010-02-24
I have just upgraded from 8.04 to 9.10.
The display worked well in 8.04.  Had some issues with 9.04 with small screen size, so upgraded to 9.10.  Now cannot get the display to work at all.

I have tried all manners of xorg.conf changes but when restarting gdm the screen flicks between a mosiac of colours and then the system locks up.  Can ony be reset by a power down.

My VGA driver is the ATI Mobility Radeon M7 7500.

I have reinstalled 8.04 on a seperate partition on the same laptop and the display works fine again.

I would be interested in how you got the dispaly configured in 9.10.

Regards

---

