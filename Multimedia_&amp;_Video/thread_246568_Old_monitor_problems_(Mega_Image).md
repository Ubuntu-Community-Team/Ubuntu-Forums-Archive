---
title: "Old monitor problems (Mega Image)"
date: 2006-08-29
forum: Multimedia &amp; Video
---

### Post by wolfdragon_2848 on 2006-08-29
I recently got a crappy PC from a friend that I decided would be my personal guinea pig. I took out an old monitor from my first computer and hooked it up to the tower. It had Win98 installed on it and everything displayed fine when I got to the desktop. Then I popped in a Ubuntu CD and installed it. However, whenever I get to the desktop, everything goes haywire. The whole screen is scrambled and I can't even tell my cursor apart from the rest of the desktop.

The monitor is a Mega Image, model # CAD14NF. We got it in 1992 so it's pretty old. Any suggestions (beyond "throw that piece of crap away") would be appreciated.

---

### Post by Sam on 2006-08-29
You need to set the correct modeline according your monitor. I've googled a bit but I found nothing (your monitor brand is not well known).

This should be something like this:
```
ModeLine        "640x480" 25.175 640 656 752 800 480 490 492 525 -hsync -vsync
ModeLine        "800x600" 40 800 840 968 1056 600 601 605 628 +hsync +vsync
ModeLine        etc..
```
you need to add in section "Monitor" in /etc/X11/xorg.conf.

---

### Post by wolfdragon_2848 on 2006-08-29
The problem is that I don't know the what modeline to use.

I found some information on a [similar model]("http://www.si87.com/MonitorSolutions/megaimage/cac14nf.html").

Also, how can I look at xorg.conf if I can't see anything discipherible on the screen?

---

### Post by Sam on 2006-08-29
> **wolfdragon_2848 said:**
> The problem is that I don't know the what modeline to use.

I found some information on a [similar model]("http://www.si87.com/MonitorSolutions/megaimage/cac14nf.html").

Also, how can I look at xorg.conf if I can't see anything discipherible on the screen?

I found this for the 14LP model. Maybe it will work. Beware, wrong modelines may destroy your monitor.

Try this first (in xorg.conf):```

Section "Monitor"
  Identifier  "Your monitor idenifier"
  HorizSync   31.5 - 48.5
  VertRefresh 50 - 90
  #Your other options below:
  #Option     "DPMS"
EndSection
```

If it don't work try this:
```
Section "Monitor"

    Identifier  "Your monitor idenifier"
    ModelName   "14LP"

# HorizSync is in kHz unless units are specified.
# HorizSync may be a comma separated list of discrete values, or a
# comma separated list of ranges of values.
# NOTE: THE VALUES HERE ARE EXAMPLES ONLY.  REFER TO YOUR MONITOR'S
# USER MANUAL FOR THE CORRECT NUMBERS.

    HorizSync   31.5 - 48.5

#    HorizSync  30-64         # multisync
#    HorizSync  31.5, 35.2    # multiple fixed sync frequencies
#    HorizSync  15-25, 30-50  # multiple ranges of sync frequencies

# VertRefresh is in Hz unless units are specified.
# VertRefresh may be a comma separated list of discrete values, or a
# comma separated list of ranges of values.
# NOTE: THE VALUES HERE ARE EXAMPLES ONLY.  REFER TO YOUR MONITOR'S
# USER MANUAL FOR THE CORRECT NUMBERS.

    VertRefresh 50-90

# Modes can be specified in two formats.  A compact one-line format, or
# a multi-line format.

# These two are equivalent

#    ModeLine "1024x768i" 45 1024 1048 1208 1264 768 776 784 817 Interlace

#    Mode "1024x768i"
#        DotClock       45
#        HTimings       1024 1048 1208 1264
#        VTimings       768 776 784 817
#        Flags          "Interlace"
#    EndMode

# This is a set of standard mode timings. Modes that are out of monitor spec
# are automatically deleted by the server (provided the HorizSync and
# VertRefresh lines are correct), so there's no immediate need to
# delete mode timings (unless particular mode timings don't work on your
# monitor). With these modes, the best standard mode that your monitor
# and video card can support for a given resolution is automatically
# used.

# 640x400 @ 70 Hz, 31.5 kHz hsync
Modeline "640x400"     25.175 640  664  760  800   400  409  411  450
# 640x480 @ 60 Hz, 31.5 kHz hsync
Modeline "640x480"     25.175 640  664  760  800   480  491  493  525
# 800x600 @ 56 Hz, 35.15 kHz hsync
ModeLine "800x600"     36     800  824  896 1024   600  601  603  625
# 1024x768 @ 87 Hz interlaced, 35.5 kHz hsync
Modeline "1024x768"    44.9  1024 1048 1208 1264   768  776  784  817 Interlace

# 640x480 @ 72 Hz, 36.5 kHz hsync
Modeline "640x480"     31.5   640  680  720  864   480  488  491  521
# 800x600 @ 60 Hz, 37.8 kHz hsync
Modeline "800x600"     40     800  880  1008 1056   600  601  605  628 +hsync 
+vsync

# 800x600 @ 72 Hz, 48.0 kHz hsync
# Modeline "800x600"     50     800  856  976 1040   600  637  643  666 +hsync 
+vsync

# 1024x768 @ 60 Hz, 48.4 kHz hsync
Modeline "1024x768"    65    1024 1064 1208 1344   768  771  777  806 -hsync 
-vsync

# 1024x768 @ 70 Hz, 56.5 kHz hsync
Modeline "1024x768"    75    1024 1048 1184 1328   768  771  777  806 -hsync 
-vsync
# 1280x1024 @ 87 Hz interlaced, 51 kHz hsync
Modeline "1280x1024"   80    1280 1296 1512 1568  1024 1025 1037 1165 Interlace

# 1024x768 @ 76 Hz, 62.5 kHz hsync
Modeline "1024x768"    85    1024 1032 1152 1360   768  784  787  823
# 1280x1024 @ 61 Hz, 64.2 kHz hsync
Modeline "1280x1024"  110    1280 1328 1512 1712  1024 1025 1028 1054

# 1280x1024 @ 74 Hz, 78.85 kHz hsync
Modeline "1280x1024"  135    1280 1312 1456 1712  1024 1027 1030 1064

# 1280x1024 @ 76 Hz, 81.13 kHz hsync
Modeline "1280x1024"  135    1280 1312 1416 1664  1024 1027 1030 1064

# Low-res Doublescan modes
# If your chipset does not support doublescan, you get a 'squashed'
# resolution like 320x400.

# 320x200 @ 70 Hz, 31.5 kHz hsync, 8:5 aspect ratio
Modeline "320x200"     12.588 320  336  384  400   200  204  205  225 Doublescan
# 320x240 @ 60 Hz, 31.5 kHz hsync, 4:3 aspect ratio
Modeline "320x240"     12.588 320  336  384  400   240  245  246  262 Doublescan
# 320x240 @ 72 Hz, 36.5 kHz hsync
Modeline "320x240"     15.750 320  336  384  400   240  244  246  262 Doublescan
# 400x300 @ 56 Hz, 35.2 kHz hsync, 4:3 aspect ratio
ModeLine "400x300"     18     400  416  448  512   300  301  602  312 Doublescan
# 400x300 @ 60 Hz, 37.8 kHz hsync
Modeline "400x300"     20     400  416  480  528   300  301  303  314 Doublescan
# 400x300 @ 72 Hz, 48.0 kHz hsync
Modeline "400x300"     25     400  424  488  520   300  319  322  333 Doublescan
# 480x300 @ 56 Hz, 35.2 kHz hsync, 8:5 aspect ratio
ModeLine "480x300"     21.656 480  496  536  616   300  301  302  312 Doublescan
# 480x300 @ 60 Hz, 37.8 kHz hsync
Modeline "480x300"     23.890 480  496  576  632   300  301  303  314 Doublescan
# 480x300 @ 63 Hz, 39.6 kHz hsync
Modeline "480x300"     25     480  496  576  632   300  301  303  314 Doublescan
# 480x300 @ 72 Hz, 48.0 kHz hsync
Modeline "480x300"     29.952 480  504  584  624   300  319  322  333 Doublescan

  #Your other options below:
  #Option     "DPMS"
EndSection
```


You said that it happens only when you enter the desktop environnement. So when Grub starts, choose "Ubuntu, kernel 2.6.xx-xx-xx (recovery mode)". You will be in the shell where you can edit your /etc/X11/xorg.conf file.

You can alse remove the harddisk, put it in an another computer and edit the file from the other computer.

---

### Post by wolfdragon_2848 on 2006-08-29
I tried the first one. It got to the logon screen except it said that the X program or whatever it's called couldn't initiate. So all I got was text, no GUI.

I can't try the second thing because it would take me too long to type in and I can't hook the hard drive up to another computer.

---

### Post by Sam on 2006-08-29
You don't need to write lines starting with a "#", these are comments (it's half lines less to write ;))

---

### Post by wolfdragon_2848 on 2006-09-09
I haven't gotten a chance to try out what you suggested yet. But I did find the manual for the monitor. Thank God my parents are pack rats. There's a whole bunch of different numbers listed but I think I've figured it out.

It says that the horizontal frequency is 31.5 and 35.5 KHz. And the vertical frequency is 70, 60, 56, and 87 Hz. So I'm assuming that the HorizSync is 31.5 - 35.5 and the VertRefresh is 56 - 87. Am I right?

---

