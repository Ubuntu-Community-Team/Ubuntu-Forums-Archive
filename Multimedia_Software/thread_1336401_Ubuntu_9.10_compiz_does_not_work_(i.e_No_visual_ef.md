---
title: "Ubuntu 9.10 compiz does not work (i.e No visual effects) and video recording poor"
date: 2009-11-24
forum: Multimedia Software
---

### Post by pmp on 2009-11-24
Hi
I have Ubuntu 9.10. Compiz does not work as I can not activate visual effects (black screen as an output.

If I give following in terminal compiz does not restart:

desktop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

I downloaded a script that checks compiz and got following output:

desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 

desktop:~$ 


Furthermore Cheese video recording does not work. I have almost still picture recorded as it is halting almost directly so I get only one movement recorded.

Skype 2 way video halts the whole machine:

Skype (2.1.0.47 via mediubuntu) crashes or freezes the whole Ubuntu 9.10 when attempting a 2 way video call. I can see a working video under video properties, before I make a call. I did not have this problem with earlier skype versions that I used in Ubuntu 9.04.

In ubuntu 9.10 I have tried to start skype with following script:

#!/bin/sh
export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype 

It did not improve the situation.

I also tried to change the generic compiz display settings (unmark detect_refresh_rate and mark the sync_to_vblank), but situation did not improve here either. (these are probably irrelevant as compiz is not working anyhow.)

Here is part of /etc/X11/xorg.conf

Section "Device"
               Identifier  "Card0"
        Driver      "radeon"
        VendorName  "ATI Technologies Inc"
        BoardName   "RV280 [Radeon 9200 PRO]"
        BusID       "PCI:1:0:0"
        Option          "AccelMethod"    "EXA"  #either XAA or EXA. "XAA" is th$
        #Option          "EnablePageFlip" "true" #only works with accelmethod "$
        #Option          "TripleBuffer"   "true" #This *might* help if you use $
        Option "AGPSize" "128"
        #Option          "XAANoOffscreenPixmaps"
        Option         "AGPMode" "1"
        Option "MigrationHeuristic" "greedy"
        Option "AccelDFS" "true"
        Option "EnableDepthMoves" "true"
EndSection


I also tried to add the option nomodeset to the kernel boot options in the grub config. But it did not change the behaviour to better or worse either.

I wonder what is broken in Ubuntu 9.10? I wonder if not working compiz, poor video recording and not working 2 way video in skype are having same root cause (Video paralyzes almost immediately in Skype as well as in Cheese). The difference between Cheese and Skype is that Cheese makes only short video, programm and computer stays stays up whereas skype stops to work and whole computer goes numb (which is rather rare experience in Linux to me until now).

Ideas would be appreciated!

---

### Post by pmp on 2009-12-04
Compiz is now working is working in my case:D. I have done the recent upgrades of Ubuntu 9.10 and did remove errors that I detected through the commands:
./compiz-check
cat /var/log/Xorg.0.log | grep EE
LIBGL_DEBUG=verbose glxinfo | grep error
or 
LIBGL_DEBUG=verbose glxinfo | head

Based on errors visible from about command outputs and some googling.


The decisive changes in /etc/X11/xorg.conf were:

        Option          "AGPSize" "64"
        Option          "AGPMode" "4"

(the nonworking values in my case were 

        Option          "AGPSize" "128"
        Option          "AGPMode" "1")

So after editing sudo nano /etc/X11/xorg.conf
and rebooting I could choose any visual effect and play with compiz config.


:D

./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]





and the other things (probably unrelated sorry):

Skype video without crashes or hanging the machine if I disable automatic start of own video sending. Start the call, make the receiving window double size and then start own video. Same procedure in every call - not too cumbersome.
Cheese is still slow with video and does not really manage to record video - don't know should I run on better HW.

---

