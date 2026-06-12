---
title: "Help! Hooked up my LCD TV as my moniter and now video quality sucks!"
date: 2010-02-04
forum: Multimedia Software
---

### Post by UPTHEPUNKS on 2010-02-04
I hooked up my laptop via monitor cable to the L.C.D. T.V. and ran a patch I found on Ubuntu forums because it wasn't showing up on the T.V. After that it asked me what screen resolution I wanted I entered it and then the screen worked! However, now when I play movies on either the T.V as a monitor or just on the laptop itself it comes out with bad video quality now. It sucks because that was the purpose of hooking up my T.V. as the monitor was to watch movies and videos I have downloaded. Please help!

---

### Post by clancymf on 2010-02-04
What is your video card and what is the resolution of the LCD?  What player are you using XBMC, VLC, etc...

---

### Post by efflandt on 2010-02-04
Besides what clancymf asks, what patch did you apply?  And what kind of cable connects the HDTV?  Best would be HDMI, DVI, or DVI to HDMI.  VGA might require adjustments using **cvt** to determine modeline, and **xrandr** to find the X name of your video, and test settings.

I just installed a 32" 1080p HDTV as a monitor connected with DVI to HDMI cable, and it generally works great.  But my 2004 computer is slow trying to display flash (Hulu) at 1080p, so that works better at 720p.  But DVDs work fine using vlc at 1080p.

---

### Post by UPTHEPUNKS on 2010-02-04
THE PATCH I FOUND WAS ON THIS THREAD [http://ubuntuforums.org/showthread.php?t=1391878&highlight=FLATSCREEN+QUALITY+VIDEO&page=2](http://ubuntuforums.org/showthread.php?t=1391878&highlight=FLATSCREEN+QUALITY+VIDEO&page=2) I DID EVERYTHING IN THIS THREAD STEP BY STEP. 
OH AND THIS IS WHAT CAME UP WITH cvr AND xrandr :

scott@scott-laptop:~$ xrandr
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   640x480        61.0  
scott@scott-laptop:~$ cvt

usage: cvt [-v|--verbose] [-r|--reduced] X Y [refresh]

 -v|--verbose : Warn about CVT standard adherance.
 -r|--reduced : Create a mode with reduced blanking (default: normal blanking).
            X : Desired horizontal resolution (multiple of 8, required).
            Y : Desired vertical resolution (required).
      refresh : Desired refresh rate (default: 60.0Hz).

Calculates VESA CVT (Coordinated Video Timing) modelines for use with X.
scott@scott-laptop:~$

---

### Post by UPTHEPUNKS on 2010-02-04
I'm not sure what my video card is or what player I use, how would i check that? 1024 x 768 is the resolution

---

### Post by sandy8925 on 2010-02-04
Run lspci in the terminal and see whether there's an Intel,ATI or Nvidia graphics card listed somewhere there. If you can't figure it out paste the output here. I connected my laptop to the TV(LCD) too and all I got was 1024x768 even though my LCD supports upto 1080i. On the other hand my laptop has an Intel graphics card so that might explain the low resolution......

@efflandt : playing 1080p video from a web browser is slow because Flash sucks. It hogs up the cpu and doesn't use gpu acceleration.

Luckily youtube and dailymotion have options for using a HTML5 player which doesn't use flash. You can try that if you want.

---

### Post by UPTHEPUNKS on 2010-02-04
This is what came up with the lspci

scott@scott-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
02:00.0 Network controller: RaLink RT2600 802.11 MIMO

---

### Post by UPTHEPUNKS on 2010-02-05
Oh and its a VGA connection

---

### Post by UPTHEPUNKS on 2010-02-07
Any suggestions?

---

### Post by UPTHEPUNKS on 2010-02-17
Anyone know somewhere i can go for advice?

---

### Post by UPTHEPUNKS on 2010-02-22
Oh and i found the manual for my tv and the lcd panel is 20" tft lcd the resolution is 1366 x 768 and the viewing angle (l/r/u/d) is 80/80/80/60

---

### Post by UPTHEPUNKS on 2010-02-22
If someone reads this at least let me know that ur stumped or having this problem too i don't know where else to post

---

