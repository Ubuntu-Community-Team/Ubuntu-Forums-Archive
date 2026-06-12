---
title: "mythtv 0.20 issues"
date: 2007-01-09
forum: Multimedia &amp; Video
---

### Post by Vincent_Lin on 2007-01-09
Dear all,

I have some issues about playing HDTV/ATSC/mplayer/NVidia issues.  Hopefully someone can share some insights with me.  

Background first
I setup mythtv 0.20 with ubuntu Edgy, using NVidia binary drivers with xvmc enabled.  
I compiled mplayer with xvmc enabled as wll.  
I have a KWorld ATSC-110 TV card.  
I was happy when I first finished all the settings and enjoyed live and recorded ATSC broadcasts on my 19" LCD monitor.  
Then I moved it down to livingroom and hooked it up with my Mitsubishi bigscreen.  
This TV set only has component input (2001-ish machine) that goes up to 1080i.  
My Nvidia 6800 has a dangle that has component output as well.
Those lines involved in xorg.conf:

Section "Monitor"
    Identifier     "Mitsubishi"
    Option "DPMS"
    Option "ModeValidation" "NoVertRefreshCheck"
#    Option "UseEDID"          "false"
    HorizSync 15 - 46
    VertRefresh 59 - 61
#    ModeLine "960x540p" 37.26 960 976 1008 1104 540 542 548 563 +hsync +vsync
#    ModeLine "in540p" 37.26 880 944 1048 1104 480 506 520 563 +hsync +vsync
    Modeline "1280x720" 66.69 1280 1304 1376 1496 720 722 724 743 +hsync +vsync
#    Modeline "1920x1080i" 182.5 1920 1952 2648 2680 1080 1102 1113 1135 -hsync -vsync
#    ModeLine "in1080i" 74.52 1760 1888 2096 2208 960 1012 1028 1126 -hsync -vsync
#    ModeLine "1080i" 74.52 1920 1952 2016 2208 1080 1084 1096 1126 -hsync -vsync
#ModeLine "ATSC-1080-59.94i" 74.176 1920 1960 2016 2200 1080 1082 1088 1125 Interlace
#ModeLine "ATSC-1080-60i" 74.25 1920 1960 2016 2200 1080 1082 1088 1125 Interlace
ModeLine "ATSC-1080-59.94p" 148.352 1920 1960 2016 2200 1080 1082 1088 1125 interlace interlace
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV41.1 [GeForce 6800]"
    Driver         "nvidia"
    Option         "TVStandard"        "HD1080i"
    Option         "UseDisplayDevice"  "TV"
    Option         "ConnectedMonitor"  "TV"
    Option         "TVOutFormat"       "COMPONENT"     
    Option         "OverScan"          "0.7"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV41.1 [GeForce 6800]"
    Monitor        "Mitsubishi"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "ATSC-1080-59.94p" "1280x720"
    EndSubSection
EndSection


Issues
1. "HD1080i" mode, as documented in NVidia xserver, is not working at all.  However, after I put in some modelines, I have 1280x720 desktop on my TV.

2. I am not able to get full 1920x1080 out of the dangle.  The best I can get is 1280x720, which is a small box in the middle of the screen.  I am still hunting for more modelines for 1080i to try.

3. Mythfrontend starts fine, but it runs a little bit slower than on LCD screen, epecially you can feel it on gl transission of photo slideshows.  I can understand it takes more efforts to send the TV signal out, but at least I know that gl is still working.  (Yes, I set mythtv to use gl) 

4. I have set mythtv/mplayer to play my video clips based on how they are encoded.  Divx files are played with -vo xv option only.  DVDs, vod files, and other mpeg2 files are played by -vo xvmc -vc ffmpeg12mc options.  This setup works perfectly on LCD monitor, but it crashes ubuntu big-time.  ubuntu usually freezes when I go into live-TV, watching recorded programs, and in watching both video clips and DVDs, regardless xv or xvmc option I use with mplay for the clips. 

5. When it freezes itself, Ctrl-Alt-F1, or Ctrl-Alt-(RightArrow) usually don't work at all.   I can ssh into this box and kill both mplayer and mythfrontend, but I have never been able to recover gnome desktop at all.

6. Worse yet, when I /etc/init.d/gdm restart, the whole system then freezes itself.  the ssh session is frozen as well.  Cold-reboot is the only way to make it work again.

Help!  If someone feels this is familiar, please share how you have resolved any of the issues.  It is really really much appreciated.

Vincent Lin

---

### Post by Vincent_Lin on 2007-01-09
Dear all,

Issues 3, 4, 5, 6 were solved by installing NVidia dirver 1.0.9746.  I simply followed the instructions from NVidia website to install it.  I then copied my old xorg.cof file over, and it is all ok about mplayer wiht xv or xvmc output, or mythtv slowness.  it's amazing!  I don't want to recall what version of NVidia driver I had before.

However, it is a long and lasting quest to find a suitable 1080i modelines for my Mitsubishi 46809, which only has component input for ATSC/HDTV stuff, and it only accepts either 540P or 1080i, not 720p.

After examining every /var/log/Xorg.0.log created by every failed try, I know that NVidia is so picky about the proper modelines, for I have disabled any possible options as interaction/handshakes between NVidia and Mitsubishi. 

Does anyone have a working Modeline for 1080i that is running on NVidia 6800 with component dangle?

Thanks a lot.

Vincent Lin

---

### Post by majoridiot on 2007-01-10
your best bet is to search/ask in the nvidia linux forums... there is a wealth of info and
solutions there from folks who have been there, done that.  the forum is also frequented by
nvidia staff who don't hesitate to jump in- it's a great resource.

[http://www.nvnews.net/vbulletin/](http://www.nvnews.net/vbulletin/)

---

### Post by Vincent_Lin on 2007-01-10
Thanks.

I was there for the last couple weeks.

Unfortunately it is not a common/popular practice these days for using NVidia buildin component hooking up TV's compoennt with HD1080i.  More and more HDTV sets are equipped with DVI or HDMI, which I believe, NVidia can directly support in settings for DFP (thus DVI output).

Actually, /var/log/Xorg.0.log says NVidia dirver always rejects my 1080i modelines, which suggests, I certainly hope, that there might be a working 1080i modeline existing out there - specific for NVidia 6800 TV out as component output at 1080i HDTV scenario.

So, the point is, if I can find it - somewhere out there, or sometime in the future.  Besides, I have not tried nvidia-setting program yet.

Thanks a lot.

Vincent Lin

---

### Post by majoridiot on 2007-01-10
from what i have found, this:

```
ModeLine "960x540p" 37.26 960 976 1008 1104 540 542 548 563 +hsync +vsync
```
is the modeline that works on that model tv.  xorg.conf settings can be very tricky, as they sometimes
conflict with each other and you never know what will win out.  since that is the modeline that
reportedly works, let's assume it's correct.  try removing all of the other commented modelines
(just to clean things up) and then we'll go at it a step at a time.

my first thought is that you have commented out the ignore edid directive and then explicitly
state h and v freq ranges... so we don't know what freqs x is trying to use, the detected edid
or the ones you define.  try uncommenting this line:

```
# Option "UseEDID" "false"
```

which will ignore the edid and use the frequencies you define.  btw- where did those freqs
come from?  did you check to see if they match what edid (might) report?

if there's no change, post your most recent xorg.conf and the xorg.0.log that results from
running it.

---

### Post by Vincent_Lin on 2007-01-10
Thanks.

1280x720  modeline was copied from some websites that do HDTV, mythtv stuff.  It just works on my setup.

The mode you recommended 960x540p did not work.  Attached zip contains files you mentioned.  Hopefully you can help me to debug it.  Edid did not work, as Xorg.0.log did not mention any spec. from  my Mitsubish 46809.

Thanks again.


Vincent Lin

---

### Post by Vincent_Lin on 2007-01-10
Dear all,

I am so excited.

Setting HDTV only needs specify HDTV modes, without any definition of modelines.

I was playing around reading Xorg.0.log and noticed that when I commented out 1280x720 modeline but still had Modes "1290x720" remained, and X still started with "Validated mode 1280x720 stated in Xorg.0.log.  So, I simply set Modes "1920x1080" without any modeline definition for 1920x1080.  And it works!!

So, the key here are that:

1. All those modelines that worked for others only because they are using either VGA or DVI interface hooking up to a HDTV set with either VGA or DVI interface.
2. When using TV out, especially component out, all you need to do is specify Modes "1920x1080" (or "180x720" whatever 540p, 720p or 1080i resolution) wthout any modeline definition for it.

Now I have to go work on TVOverscan issue.  It is really complete ignored by NVidia driver, as shown in actually display screen and Xorg.0.log.   However, I have read some posts somewhere that creating Gnome panels with appropriate sizes at the border of the the screen can squeeze the application to be placed in the middle with good size. 

Also it is mentioned that mythtv can specify the screen size when it is running, which feature is designed accomodate this overscan issue.

Another issue is audio stutter while viewing ATSC broadcasting.  I hope latest v4l driver for my KWorld ATSC-110 card, as well as latest ALSA driver can help me.  It's only a matter of re-compilation. 

Overall, I am extremely happy and excited.

Thanks all that helped.

Vincent Lin

---

### Post by majoridiot on 2007-01-10
glad you got it working!

and thanks for coming back to share your solution :D

---

### Post by Vincent_Lin on 2007-01-11
You are welcome.

I always jumped into conclusion easily.

Yeah, I have another issue.

The download and install of NVidia 1.0.9746 driver said "precompiled kernel interface not found."  and it wanted to downlaod a kernel interface and then it actually compiled a kernel interface for me.  It then build kernel module for me, evantually claiming that it is installed. 
Then sudo /etc/init.d/gdm restart works.  But this would not survive a reboot, which means that I have to run "sudo sh NVIDIA-Linux-x86-1.0-9745-pkg1.run" again and gdm to start it up.  /var/log/Xorg.0.log" says 

(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Any idea?  It seems some kernel modules are loaded.  Who are they?  And what should I do the load them?  In /etc/modules?

Thanks.

Vincent Lin

---

### Post by superm1 on 2007-01-12
> **Vincent_Lin said:**
> You are welcome.

I always jumped into conclusion easily.

Yeah, I have another issue.

The download and install of NVidia 1.0.9746 driver said "precompiled kernel interface not found."  and it wanted to downlaod a kernel interface and then it actually compiled a kernel interface for me.  It then build kernel module for me, evantually claiming that it is installed. 
Then sudo /etc/init.d/gdm restart works.  But this would not survive a reboot, which means that I have to run "sudo sh NVIDIA-Linux-x86-1.0-9745-pkg1.run" again and gdm to start it up.  /var/log/Xorg.0.log" says 

(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Any idea?  It seems some kernel modules are loaded.  Who are they?  And what should I do the load them?  In /etc/modules?

Thanks.

Vincent Lin
Two problems I can think of.  
Did u disable the nvidia driver in linux-restricted-modules from loading in /etc/default/linux-restricted-modules-common?

Did you run depmod -a after the install?

---

### Post by Vincent_Lin on 2007-01-12
Thanks.

1. I did not do anything before I ran sudo sh NVIDIA*.run.  I will try to disable nvidia module loading, before I install it again.  Am I picking up the right way of doing it?

2. NVidia installation stript has a part of running depmod -a, as it shows on the terminal while installing it.


Thanks again.  Will let you all know.

Vincent Lin

---

### Post by superm1 on 2007-01-12
> **Vincent_Lin said:**
> Thanks.

1. I did not do anything before I ran sudo sh NVIDIA*.run.  I will try to disable nvidia module loading, before I install it again.  Am I picking up the right way of doing it?

2. NVidia installation stript has a part of running depmod -a, as it shows on the terminal while installing it.


Thanks again.  Will let you all know.

Vincent Lin
Vincent,
To disable the nvidia module from loading, you edit /etc/default/linux-restricted-modules-common.  Add "nv" to the DISABLED_MODULES line.

---

### Post by Vincent_Lin on 2007-01-13
Hi,

I did as you told me - add "nv" into that line.  Now it works.  

Thanks a lot.

Vincent

---

