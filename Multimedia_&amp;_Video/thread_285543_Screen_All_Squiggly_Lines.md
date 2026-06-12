---
title: "Screen All Squiggly Lines?"
date: 2006-10-26
forum: Multimedia &amp; Video
---

### Post by lordfoul on 2006-10-26
I've installed Parallels on xp and am running Vista RC2 just fine but all the linux distro's i've tried to install work fine until I try to boot in and then I get "squiggley lines" and can't seem to fix this. I am using an lcd with a native res of 1680x1050; any advice would be appreciated to help me get Ubuntu working properly.

The error Parallels gives is

Screen resolution requested by guest operating system can not be set because it is not supported by the host hardware (either display or video adapter). Please reduce guest operating system resolution or/and color depth.

---

### Post by hopstah on 2006-10-26
the problem is (probably) that you are running your windows at 32 bit color, when linux defaults to 24 bit, and doesn't even support 32 bit.  try setting your host operating system to 24 bit and see if that helps.

---

### Post by lordfoul on 2006-10-27
I am unable to set it to 24bit res my only options are 8,16 and 32.  I tried 16 bit res to no avail.  Any way force a resolution on install perhaps?  Some one on the parallels forum suggested it is my horz and vert frequency settings, but I have no idea how I'd adjust that.

Here are my monitors specs...

LG L203WT-BF

Sync Input
Horizontal Freq 28-83kHz (Automatic)
Vertical Freq 56-85Hz (Automatic)

Preset Modes (Resolution) Horiz Freq. (kHz) Vert Freq. (Hz)
1 720 x 400 31.468 70

2 640 x 480 31.469 60

3 640 x 480 37.500 75

4 800 x 600 37.897 60

5 800 x 600 46.875 75

6 1024 x 768 48.363 60

7 1024 x 768 60.123 75

8 1152 x 864 67.500 75

9 1280 x 1024 63.981 60

10 1280 x 1024 79.976 75

*11 1680 x 1050 64.674 60

**12 1680 x 1050 65.290 60

* Digital Recommend Mode
** Analog Recommend Mode

---

### Post by handy on 2006-10-28
Hi, firstly what kind of graphic card do you have & do you have the appropriate drivers installed for it?

If you could post a copy of your

**/etc/X11/xorg.conf**

I/We (depending on the timing) can help you set it up.

What follows is the section of the **xorg.conf** where you put your monitor's refresh rates:
____________________
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       ***_30.0_*** - ***_107.0_***
    VertRefresh     ***_48.0_*** - ***_120.0_***
    Option         "DPMS"
EndSection
____________________

Replace the **_Bold Underlined_** numbers with **your monitor's** respective horizontal & vertical refresh rates, don't change anything else in that section.

But really without knowing where you are up to with your graphics card driver's, doing anything first could just be a waste of time because it could get overwritten anyway! :)

---

