---
title: "ATI Tv-Out is BLACK AND WHITE!!?"
date: 2006-02-02
forum: Multimedia &amp; Video
---

### Post by AlternativeS on 2006-02-02
Hi everyone, I just have one question

I just acquired an ATI RADEON9800 from a friend.  I've got Tv-Out working, but its only in black and white.  I'm in the United States, so I have it set to output NTSC-M.  What is going on?  I really want color.  Could it be because I was previously using an Nvidia (5200)?

Please help, I appreciate it.

---

### Post by AlternativeS on 2006-02-03
bump

---

### Post by GuruX on 2006-02-04
Are you sure that the computer is the problem? Sometimes old tvs won't give you anything else than black and white over composite.

---

### Post by krusbjorn on 2006-02-04
You probably set the TV out format to "S-VIDEO" when it's supposed to be "composite", or the other way around. Just change it in your /etc/X11/xorg.conf, restart your x server and it should be okay.

---

### Post by LifeIsAFractal on 2006-02-08
I've had this problem in the past with windows and Linux.  The culprit ended up being my s-video to rca converter.  It just plain wouldn't work with my vid card.  If you are using one of those try a different one.

---

### Post by erider on 2006-06-22
I had the same problem and solved it setting the tv to AUTO instead of NTSC

---

### Post by mkljun on 2006-07-16
I had the same problem which took me 5 hours to solve. I wanted my screen to be extended on my 2nd monitor (TV) so when someone would work on a PC I would be able to watch a movie on a TV. An I wanted colors :)

I have Pc and TV connected with S-VIDEO cable this way:
PC <-> S-VIDEO <-> S-VIDEO/SCART converter <-> TV

Here's my device section from xorg.conf

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
        # ########## disable PnP Monitor  ##########
	Option	    "HWcursor" "yes"
	# ### generic DRI settings ###
	Option	    "NoTV" "no"
	Option	    "TVFormat" "PAL-G"
	Option	    "TVStandard" "COMPOSITE"
	Option	    "TVHSizeAdj" "0"
	Option	    "TVVSizeAdj" "0"
	Option	    "TVHPosAdj" "0"
	Option	    "TVVPosAdj" "0"
	Option	    "TVHStartAdj" "0"
	Option	    "TVColorAdj" "0"
	Option	    "GammaCorrectionI" "0x06419064"
	Option	    "GammaCorrectionII" "0x06419064"
        # this extends monitor to the right
	Option	    "DesktopSetup" "0x00000200"
	Option	    "MonitorLayout" "AUTO, AUTO"
EndSection

Set format and standard to your needs. aticonfig has following options:

TV Options:
  --tvf, --tv-format-type=STRING
        Change the TV signal format.  STRING can be one of:
            NTSC-M
            NTSC-JPN
            PAL-B
            PAL-D
            PAL-G
            PAL-H
            PAL-I
            PAL-K
            PAL-K1
            PAL-L
            PAL-M
            PAL-N
            PAL-CN
            PAL-SCART
  --tvs, --tv-standard-type=STRING
        Change the TV standard for TV output.  STRING can be one of:
            VIDEO
            SCART
            YUV


Hope this help.

lp mk

---

### Post by kogber on 2006-12-23
I ran into the same issue when I installed the ATI driver.  This aticonfig command fix worked for me:

$ sudo aticonfig --tv-format-type=NTSC-M

then restart the pc.

My setup is a dual-head "extended desktop" with a composite line going to the tv via a S-video to composite adapter for an ATI radeon X800 GTO

---

