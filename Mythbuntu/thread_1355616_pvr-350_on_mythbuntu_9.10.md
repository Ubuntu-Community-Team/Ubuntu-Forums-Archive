---
title: "pvr-350 on mythbuntu 9.10"
date: 2009-12-15
forum: Mythbuntu
---

### Post by hylsan on 2009-12-15
Does anyone running a pvr-350 on 9.10?
I've tried to follow this since its the latest [**HOW-TO**]("https://help.ubuntu.com/community/MythTV_Jaunty_hardware_pvr-350_TV-out")

Running the first things I get this;
```

tomas@MythCube:~$ lsmod | grep ivtvfb
tomas@MythCube:~$ sudo modprobe ivtvfb
[sudo] password for tomas: 
WARNING: All config files need .conf: /etc/modprobe.d/aliases, it will be ignored in a future release.
tomas@MythCube:~$ 

```

I installed this a couple of weeks ago and I think I came as far as getting live-tv on tv-out, but then I tried to get X on tv-out and now nothing works.

Hope anyone can help me.

edit: ok, the live-tv on tv-out DOES work...but X still dont work..

/Hylsan

---

### Post by huzzak on 2010-01-03
Hylsan,

I'm trying to get things going with Mythbuntu 9.10 and my PVR-350 card.  I can't get tv-out to work with Mythtv.

The output when I try to watch tv with the PVR-350 playback enabled is as follows:

> 2010-01-03 20:07:34.330 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- begin
2010-01-03 20:07:34.422 Opening audio device 'default'. ch 2(2) sr 44100
2010-01-03 20:07:34.422 Opening ALSA audio device 'default'.
2010-01-03 20:07:34.458 Mixer unable to find control Master
2010-01-03 20:07:34.459 Mixer unable to find control Master
2010-01-03 20:07:34.460 NVP(0): Enabling Audio
2010-01-03 20:07:34.483 IVD: ivtv version 1.4.1
2010-01-03 20:07:34.483 IVD Error: Failed to locate framebuffer
			Did you load the ivtv-fb Linux kernel module?
2010-01-03 20:07:34.483 VideoOutput, Error: Not compiled with any useable video output method.
2010-01-03 20:07:34.483 NVP(0), Error: Couldn't create VideoOutput instance. Exiting..
2010-01-03 20:07:34.483 Unable to initialize video.
2010-01-03 20:07:54.474 playCtx, Error: StartDecoderThread() Failed to startdecoder
2010-01-03 20:07:54.474 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- end error
2010-01-03 20:07:54.474 TV Error: LiveTV not successfully started
2010-01-03 20:07:54.475 ScreenSaverX11Private: DPMS Deactivated 1
2010-01-03 20:07:54.483 ScreenSaverX11Private: DPMS Reactivated 1


It can't find ivtv-fb?  Do you have any insights from your own experience?  Thanks!

Huzzak.

---

### Post by huzzak on 2010-01-04
Update!  I installed ivtv-utils per the discussion [here]("https://help.ubuntu.com/community/MythTV_Intrepid_hardware_pvr-350_TV-out") and rebooted and now I get sound and video through the television.  Awesome!

I'm still somewhat puzzled about getting X to display through the PVR-350.  [This guide]("https://help.ubuntu.com/community/MythTV_Intrepid_hardware_pvr-350_TV-out") and [this guide]("https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out") suggest that I modify /etc/X11/xorg.conf and this is what I did when I setup Mythbuntu 8.04, but I can't find xorg.conf on Mythbuntu 9.10.

Does anyone know how this needs to be set up in Mythbuntu 9.10?  Thanks!

Huzzak.

---

### Post by hylsan on 2010-01-04
nice you got it to work so far atleast.

Strange about the xorg.conf, cant remember having any trouble find it on my system. 

Still cant get X to work tho. :(

/Hylsan

---

### Post by huzzak on 2010-01-04
It looks like Ubuntu 9.10 "abandoned" the xorg.conf file according to [this thread]("http://ubuntuforums.org/showthread.php?t=1339048"), though it can be placed in /etc/X11/xorg.conf and it will be found and used.

Accordingly, I tried to use the xorg.conf for Jaunty that I found [here]("https://help.ubuntu.com/community/MythTV_Jaunty_hardware_pvr-350_TV-out") and the xorg.conf I found [here]("http://ubuntuforums.org/showthread.php?t=780229&page=3") from gfowler that worked when I was running Mythbuntu 8.04.  Neither worked (I had to start up in safe mode) but the second wouldn't even parse so I guess there have been some significant changes since Mythbuntu 8.04.

Any ideas or suggestions about what I might try next?

---

### Post by gfowler on 2010-01-04
> **huzzak said:**
> It looks like Ubuntu 9.10 "abandoned" the xorg.conf file according to [this thread]("http://ubuntuforums.org/showthread.php?t=1339048"), though it can be placed in /etc/X11/xorg.conf and it will be found and used.

Accordingly, I tried to use the xorg.conf for Jaunty that I found [here]("https://help.ubuntu.com/community/MythTV_Jaunty_hardware_pvr-350_TV-out") and the xorg.conf I found [here]("http://ubuntuforums.org/showthread.php?t=780229&page=3") from gfowler that worked when I was running Mythbuntu 8.04.  Neither worked (I had to start up in safe mode) but the second wouldn't even parse so I guess there have been some significant changes since Mythbuntu 8.04.

Any ideas or suggestions about what I might try next?

I just did a clean install of 9.10 to my old hardware and used the xorg.conf I had in the 8.04 install.  I needed to change the fb setting as for what ever reason it changed from 0 to 1 but otherwise it was the same.  There are some issues with lirc that you might need to address if you are using a serial blaster to control an STB.
Good luck
Jerry

---

### Post by dongajda on 2010-01-04
Hi All, 

I'm also struggling to get X working on the TV-out of my PVR-350. I've got Live-tv working and I can watch my recordings - but no X :-(

Gfowler: Could we see you xorg.conf please? I'm in desperate need of inspiration :-)

---

### Post by huzzak on 2010-01-04
I had to change the fb from 0 to 1 as well (inteldrmfb is the new 0 in /proc/fb).  This is the xorg.conf file I used, though it wasn't indented when I tried to run it earlier.  Maybe that caused the parsing error?  I'll try again with the indented file tonight.

```

#Jerry Test Config 1
Section "Monitor"
	Identifier "NTSC Monitor"
	HorizSync 30-68
	VertRefresh 50-120
	Mode "720x480"
		# D: 34.563 MHz, H: 37.244 kHz, V: 73.897 Hz
		DotClock 34.564
		HTimings 720 752 840 928
		VTimings 480 484 488 504
		Flags "-HSync" "-VSync"
	EndMode
EndSection

Section "InputDevice"
	Identifier "Generic Keyboard"
	Driver "kbd"
	Option "XkbRules" "xorg"
	Option "XkbModel" "pc105"
	Option "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
EndSection

Section "Device"
	Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"
	Driver "ivtv"
	Option "fbdev" "/dev/fb1" # <-- Obtained cat proc/fb
	Option "TVStandard" "NTSC-M"
	Option "VideoOverylay" "on"
	Option "XVideo" "1"
	BusID "3:1:0" # <-- obtain from lspci
EndSection

Section "Screen"
	Identifier "TV Screen"
	Device "Hauppauge PVR 350 iTVC15 Framebuffer"
	Monitor "NTSC Monitor" # <-- select for NTSC
	DefaultDepth 24
	DefaultFbbpp 32
	Subsection "Display"
		Depth 24
		FbBpp 32
		Modes "720x480" # <-- select for NTSC
	EndSubsection
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	Screen 0 "TV Screen" 0 0
EndSection

#Added from forum, may not need: Jerry
Section "Module"
	Load "glx"
	Load "GLcore"
	Load "dri"
	Load "v4l"
EndSection

Section "DRI"
	Group "video"
	Mode 0666
EndSection

```

Thanks for posting, gfowler.  Your success lets me know it is possible.

Huzzak.

---

### Post by gfowler on 2010-01-04
> **dongajda said:**
> Hi All, 

I'm also struggling to get X working on the TV-out of my PVR-350. I've got Live-tv working and I can watch my recordings - but no X :-(

Gfowler: Could we see you xorg.conf please? I'm in desperate need of inspiration :-)

What huzzak posted is exactly my xorg.conf file.  The only thing I changed was the fb1 as that changed for unk reasons.  I just copied it directly and made that change.  You exceeded my pay grade now :).

Jerry

---

### Post by huzzak on 2010-01-04
Awesomeness, everybody!  Apparently the tabs *do* make a difference.  X now shows up on my television screen!  Thanks for everybody's help!

Huzzak.

---

### Post by hylsan on 2010-01-05
nice you got it to work! :popcorn:

I'll try that xorg.conf tomorrow and see if it works for me too.

/Hylsan

---

### Post by dongajda on 2010-01-05
Thanks for posting the xorg.conf. It actually looks quite a bit like my own (apart from some PAL specific changes - and my mythbuntu-box is using /dev/fb0). 
What I was missing was that X was complaining that /dev/fb0 was not existing. I figured that could be because the ivtvfb module was loading too late in the boot process. to make sure the module was loaded before X was starting up I wrote the line:

modprobe ivtvfb 

near the top of "/etc/init.d/x11-common" - and Voila! X on the old crt "boob tube". 

Now I have to fix some overscan issues :-)

Thanks guys.

---

### Post by hylsan on 2010-01-05
Can you post your PAL-version of the xorg.conf please?

/Hylsan

---

### Post by dongajda on 2010-01-05
Sure - I will do so tonight.

-- 
Frank

---

### Post by dongajda on 2010-01-05
Hi all, 

As promised my xorg.conf with a PAL twist. 
Please note: It is not perfect. I still have some issues with keyboard and mouse - but that may very well be related to my hardware. The xorg.conf does however do what I want it to, namely route X to the TV-out (on my box anyway):

```
 
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"
        Driver "ivtv"
        Option "fbdev" "/dev/fb0"
        BusID "PCI:1:9:0"
EndSection

# for pal users:
Section "Monitor"
        Identifier  "TV"
        HorizSync  30-68
        VertRefresh 50-120
        Mode "720x576"
                #D: 41.475 MHz, H: 44.693 kHz, V: 74.488 Hz
                DotClock 41.476
                HTimings 720 752 840 928
                VTimings 576 580 584 600
                Flags    "-HSync" "-VSync"
        EndMode

EndSection

Section "Screen"
        Identifier "TV Screen"
        Device "Hauppauge PVR 350 iTVC15 Framebuffer"
        Monitor "TV"
        DefaultDepth 24
        DefaultFbbpp 32
        Subsection "Display"
              Depth 24
              FbBpp 32
              Modes "720x576"
        EndSubsection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "TV Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```I completely removed the "Modules" and "DRI" sections - looking through the Xorg.0.log it seems that the relevant modules are loading anyway.

---

### Post by DarrenCT on 2010-07-20
anyone know if this works on mythbuntu 10.04 install?  I'm trying to get my PVR-350 to do video out to my tv.  I was using Knoppmyth R5.5 before, but now want the ability to use Boxee as well which MythBuntu will provide.

---

