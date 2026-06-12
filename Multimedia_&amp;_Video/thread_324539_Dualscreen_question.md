---
title: "Dualscreen question"
date: 2006-12-23
forum: Multimedia &amp; Video
---

### Post by Cene on 2006-12-23
Hi

I got a small question to what I couldn't find any answers anywhere.
I have nVidia FX5200 and two CRT's (1280*1024 both = 2560*1024 @ 24bit) using TwinView. When I play any fullscreen game (i.e. DoD 1.3 thru Steam using Cedega), the other screen turns off, so I got only 1 screen with fullscreen game running.

Is it possible that when I run any fullscreen app, the CRT 1 would run the game at fullscreen in the resolution it is set at the game, while screen 2 would keep 1280*1024 and show everything during the game there was before too.
What I mean, is it possible to "cheat" fullscreen apps to think that there exists resolution 800*600 when it really is 800*600 in first screen (where the game runs) and 1280*1024 in second screen?

I usually use 1024*768 or 800*600 resolution in games. Here's my xorg.conf:

```

Section "Device"
        Identifier      "NVIDIA[0]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "TwinView"      "true"
        Option          "UseEdidFreqs"  "true"
        Option          "MetaModes" "1280x1024,1280x1024;1024x768,NULL;800x600,NULL;640x480,640x480"
        Option          "NvAGP" "1"
EndSection

Section "Monitor"
        Identifier      "Monitor[0]"
        Option          "DPMS"
        HorizSync       30-65
        VertRefresh     50-120
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA[0]"
        Monitor         "Monitor[0]"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "2560x1024" "1024x768" "800x600" "1280x480"
        EndSubSection
EndSection

```

What do I need to change or add if it's possible?

---

### Post by Cene on 2006-12-24
Anyone? :(

---

### Post by Cene on 2006-12-24
Bump. Anyone?

---

### Post by Cene on 2006-12-25
Bump.

---

### Post by Cene on 2006-12-26
>_>

---

### Post by Cene on 2006-12-27
<_<

---

### Post by majoridiot on 2006-12-27
first, it is considered extremely rude to bump a thread as often as you have- give it time,
especially during the holidays like this.. people are away or otherwise occupied.

second, i doubt you will be able to do what you are asking.  in my experience, resolution
switching for games as you specify generally wipes out the second monitor, as the game 
takes control of the desktop from the windows server/manager and does as it likes.  the 
second monitor will either remain frozen, be corrupted or display garbage due to res change, 
changes in video ram, etc.  this holds true for both windows and linux.

as i said, from my experience... if this is incorect, someone should jump in.

---

### Post by Cene on 2006-12-27
> **majoridiot said:**
> first, it is considered extremely rude to bump a thread as often as you have- give it time,
especially during the holidays like this.. people are away or otherwise occupied.

Sorry, I know. I'd just need an answer ASAP for one reason. It's a long story tho, so I haven't got time (or interest) to write it here. And there was at least 12 hours between any bump. I also know that it isn't much, but just to mention that I didn't bump it every hour or so. Thread had always fallen past page two or three.

> 
second, i doubt you will be able to do what you are asking.  in my experience, resolution
switching for games as you specify generally wipes out the second monitor, as the game 
takes control of the desktop from the windows server/manager and does as it likes.  the 
second monitor will either remain frozen, be corrupted or display garbage due to res change, 
changes in video ram, etc.  this holds true for both windows and linux.

as i said, from my experience... if this is incorect, someone should jump in.
My friend has that kind of setup 100% working on WinXP machine, so at least in Windows it's possible.

---

