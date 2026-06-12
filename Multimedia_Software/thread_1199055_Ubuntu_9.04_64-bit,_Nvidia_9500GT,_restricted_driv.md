---
title: "Ubuntu 9.04 64-bit, Nvidia 9500GT, restricted drivers"
date: 2009-06-28
forum: Multimedia Software
---

### Post by Vasator on 2009-06-28
Okay here is my issue. I have just purchased a new video card for my system and this one works with Ubuntu 9.04.
However I cannot get the restricted drivers to work.

Here is my Hardware Specifications:

Gigabyte GA-MA69VM-S2 Motherboard
AMD64 4000+ 
8GB of DDR2 800Mhz RAM
Gigabyte Nvidia GeForce 9500GT 1GB GDDR2 Memory (GV-N95TOC-1Gl)
LG Flatron W2252TQ 22" Wide screen Flat Panel
Saitek Eclipse K/B and Kensington Expert Mouse

I am running 9.04 64-bit

I assume that I cam currently running with the Open Source Drivers as the card is working.
The issue I am currently presented with is when I install the restricted drivers and reboot
I am welcomed with no sound and no video. In fact my Monitor falls asleep.
I can boot into safe mode and rebuild the x-server without issue and I am back up.

I am currently running at 1680X1250 resolution
but would love to have full 3-d accelleration as i did with my old video card in 8.10

When the system boots up  I do see the Ubuntu logo with the bar that goes from the left to the right 
as soon as that disappears the screen flickers as if resetting the resolution and then a few seconds 
later the monitor goes into standby.

***Note***
This system was not a fresh install. I upgraded from 8.10 to see if the video card would work
with 9.04 and it does so I have no need for 8.10 now (hopefully)

I do however have the 9.04 CD burned and ready to do a complete reinstall if the need arises
***End Note***


```
sudo lspci | grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9500 GT (rev a1)

grep -i driver /etc/X11/xorg.conf
Blank Response
```

Contects of Xorg.conf

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
```

Troublshooting (Googled -> Ubuntu 9.04 black screen)

Most issues were relating to the CD not being burned properly
Checked the CD with an MD5 Checksum and they match

(Googled -> Geforce 9500gt Ubuntu 9.04)

Trying this: [http://ubuntuforums.org/showthread.php?t=1035873](http://ubuntuforums.org/showthread.php?t=1035873)

Issue Persists

I have installed EnvyNG and have used it to attempt to install the drivers
It states that both recommended and compatable are the 180.44-0ubuntu1 drivers

Here is a look at the xorg.conf that is generated:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
EndSection
```

However when I reboot the machine I am greeted with the same issue.

So then I reconfigure X server and start over
This attempt I go into System -> Administration -> Hardware Drivers
and select the Nvidia Drivers (Version 180 and Version 173)

Here is the xorg.conf file after performing the above:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

So I reboot again and issue persists...

I have gone through the Ubuntu forums and found these postings:

[http://ubuntuforums.org/showthread.php?t=1192368&highlight=geforce+9500GT](http://ubuntuforums.org/showthread.php?t=1192368&highlight=geforce+9500GT)

This post reflected that the person could not play videos and did not relate to my issue

[http://ubuntuforums.org/showthread.php?t=1168184&highlight=geforce+9500GT](http://ubuntuforums.org/showthread.php?t=1168184&highlight=geforce+9500GT)

This post was more of a question than a problem. Does not relate.

[http://ubuntuforums.org/showthread.php?t=1107304&highlight=geforce+9500GT](http://ubuntuforums.org/showthread.php?t=1107304&highlight=geforce+9500GT)

This post does not fix the issue see troubleshooting.

[http://ubuntuforums.org/showthread.php?t=971317&highlight=geforce+9500GT](http://ubuntuforums.org/showthread.php?t=971317&highlight=geforce+9500GT)
[http://ubuntuforums.org/showthread.php?t=1096867&highlight=geforce+9500GT](http://ubuntuforums.org/showthread.php?t=1096867&highlight=geforce+9500GT)
[http://ubuntuforums.org/showthread.php?t=1090146&highlight=geforce+9500GT](http://ubuntuforums.org/showthread.php?t=1090146&highlight=geforce+9500GT)
[http://ubuntuforums.org/showthread.php?t=1029802&highlight=geforce+9500GT](http://ubuntuforums.org/showthread.php?t=1029802&highlight=geforce+9500GT)

Basically all the same answer but does not work.

Now I do remember hunting this issue down on another machine and I was wondering.
I am utilizing the VGA connector on the card and not the DVI. 
Could the drivers be switching to the DVI connector accidentally?
I do not have a DVI cable to test this out.

Any assistance would be greatly appreciated

Alex

---

### Post by Vasator on 2009-06-28
Just attempted this:

[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

Completely failed! Went into low resolution mode.

---

### Post by Vasator on 2009-06-28
Tested the DVI connector with a dvi-vga converter and video is not being sent to the DVI port.

I am going to stop by the store later today and am going to pick up a dvi cable and see if it helps.

---

### Post by Vasator on 2009-06-29
Tested the new DVI cable. Issue persists. I also seem to be the only person posting in my post....

---

### Post by Vasator on 2009-06-29
Just did a complete re-install with a format of the drive I am booting from. 
Run update manager 
installed all updates
rebooted
logged back in
went to System -> Admin -> Hardware Drivers
Installed the latest drivers
rebooted
Ubuntu Logo with bar going from left to right
Screen flickers (backlight still on)
Screen Flickers again (backlight slowly turns off)
Screen flickers again (Digital power save mode turns on)
Monitor goes to sleep
No sound is played from the headphones

It seems to me Ubuntu is not as good as I thought it was when on install there are problems running the video.

If I can't figure this out I will have no other choice than to install Windows 64-bit edition which I really do not want to do.

Someone please assist me

---

### Post by HappyFeet on 2009-06-29
I am using the same video card and motherboard as you, and have no problems. The only differences are the CPU, monitor and RAM, but those should not make a difference. I am actually running dual monitors beautifully. I used the 180 nvidia drivers.

Have you run diagnostic software on your hardware?

Me and a friend both built our pc's at the same time with identical parts, and he also is not having any problems. Sounds like you got a bad piece of hardware. Try memtest first.

---

### Post by Vasator on 2009-06-29
Thank you for responding....

I've run memtest and have not found any errors on the system. The funny thing is the card works flawlessly in Windows XP 64 so I doubt very highly that it is an error with the video card.

Is there a file that I can find on the system that is similar to bootlog.txt in windows that I could use to see where the system is shutting down.

Again this being a hardware failure is really not the issue. I have enough knowhow to know the difference between a hardware failure and a software failure and this is pointing to a software failure.

---

### Post by Vasator on 2009-06-29
Hey Happyfeet could you post your xorg.conf file for me?

---

### Post by Vasator on 2009-06-29
I tried the xorg.conf file you sent me and I edited out the lines that relate to the dual monitor support and the same issue persisted

---

### Post by ShOuT1 on 2009-06-29
I am having problems with a Nvidia Geforce 8200 card with 9.04 64 bit.  Only I get a screen that flashes repeatedly after log in.  I installed 8.04.2 to see if it was any better and when I tried the restricted drivers with it, X broke completely.   I too have looked at a bunch of other forums, but none have helped to this point.

---

### Post by Vasator on 2009-06-30
Okay after messing with the setting I am now getting an error message on boot about the Nvidia Drivers failing to load and running in low resolution.

Still working on fixing this after three days

---

### Post by Vasator on 2009-07-01
Update:

I decided to test and see if the issue is the card.

Created a 20GB partition for XP 64-bit
Installed all drivers and updates
Only issue is occasional crashes with Second Life

Created the 2nd Partition for Ubuntu 9.04
updated the machine, attempted to install the 180 drivers

System->Admin->Hardware Drivers
selected the 180 drivers
Went into Synaptic
Verified that everything Nvidia 180 was selected
Rebooted
(Got these instructions in SL from the Ubuntu Users Group)

Received the ssame issue that has plagued me in the beginning
I see the Ubuntu Logo with the bar below it going left->right
Screen flickers as if changing screen resolution
Monitor goes into sleep mode
System Crashed - No keyboard/mouse nothing
Attempted to jump inot terminal CTRL-ALT-F1 -> Nothing

I reboot (I've had my drive scanned about 10 times now with fsck)
select "safe mode" and run xfix utility and I have video again.

I have scoured this forum, linux qyestions, google to no avail.

I have come close though and am not giving up.

---

### Post by rs3 on 2009-07-03
> **Vasator said:**
> Is there a file that I can find on the system that is similar to bootlog.txt in windows that I could use to see where the system is shutting down.

Yes; the last attempted execution of X.org should log to /var/log/Xorg.0.log

If you're able to post the results of this log, we can hopefully discern what goes wrong when starting with the proprietary drivers.  Errors will begin with an (EE) in the line.

I commend your persistence!  It's very unusual to have difficulties such as these.  I built a few systems using NVidia drivers since 5.10 and have generally only had issues with botched driver installation.

I'm apt to guess you have already grabbed the latest series of updates before attempting this?  I did have a couple odd, sporadic crashes with the kernel that shipped with 9.04 and the proprietary driver (180); there have been at least a couple kernel updates since the release, and they should be available via Update Manager.

---

### Post by Vasator on 2009-07-03
Okay updates since my last post:

Installed XP 64-bit onto a 20GB partition
Installed Ubuntu 9.04 64-bit onto the rest

I wanted to wait to see if anyone had replied to this post before messing around with the system.

Contents of /var/log/Xorg.0.log (This is the working Config)

```
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.635 redY: 0.342   greenX: 0.292 greenY: 0.611
(II) NV(0): blueX: 0.147 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): 1152x870@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Ranges: V min: 56 V max: 75 Hz, H min: 28 H max: 83 kHz, PixClock max 150 MHz
(II) NV(0): Monitor name: W2252
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff001e6d7e5624fd0000
(II) NV(0): 	02120103ea312078eaaec5a2574a9c25
(II) NV(0): 	125054a76b80950081808140714f0101
(II) NV(0): 	0101010101017c2e90a0601a1e403020
(II) NV(0): 	3600da281100001a21399030621a2740
(II) NV(0): 	68b03600da281100001c000000fd0038
(II) NV(0): 	4b1c530f000a202020202020000000fc
(II) NV(0): 	0057323235320a202020202020200044
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): EDID vendor "GSM", prod id 22142
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NV(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NV(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NV(0): EDID vendor "GSM", prod id 22142
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): Probing for EDID on I2C bus 2...
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus 0...
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: GSM  Model: 567e  Serial#: 64804
(II) NV(0): Year: 2008  Week: 2
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 49  vert.: 32
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.635 redY: 0.342   greenX: 0.292 greenY: 0.611
(II) NV(0): blueX: 0.147 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): 1152x870@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Ranges: V min: 56 V max: 75 Hz, H min: 28 H max: 83 kHz, PixClock max 150 MHz
(II) NV(0): Monitor name: W2252
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff001e6d7e5624fd0000
(II) NV(0): 	02120103ea312078eaaec5a2574a9c25
(II) NV(0): 	125054a76b80950081808140714f0101
(II) NV(0): 	0101010101017c2e90a0601a1e403020
(II) NV(0): 	3600da281100001a21399030621a2740
(II) NV(0): 	68b03600da281100001c000000fd0038
(II) NV(0): 	4b1c530f000a202020202020000000fc
(II) NV(0): 	0057323235320a202020202020200044
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): EDID vendor "GSM", prod id 22142
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NV(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NV(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NV(0): EDID vendor "GSM", prod id 22142
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): Probing for EDID on I2C bus 2...
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus 0...
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: GSM  Model: 567e  Serial#: 64804
(II) NV(0): Year: 2008  Week: 2
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 49  vert.: 32
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.635 redY: 0.342   greenX: 0.292 greenY: 0.611
(II) NV(0): blueX: 0.147 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): 1152x870@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Ranges: V min: 56 V max: 75 Hz, H min: 28 H max: 83 kHz, PixClock max 150 MHz
(II) NV(0): Monitor name: W2252
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff001e6d7e5624fd0000
(II) NV(0): 	02120103ea312078eaaec5a2574a9c25
(II) NV(0): 	125054a76b80950081808140714f0101
(II) NV(0): 	0101010101017c2e90a0601a1e403020
(II) NV(0): 	3600da281100001a21399030621a2740
(II) NV(0): 	68b03600da281100001c000000fd0038
(II) NV(0): 	4b1c530f000a202020202020000000fc
(II) NV(0): 	0057323235320a202020202020200044
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): EDID vendor "GSM", prod id 22142
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NV(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NV(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NV(0): EDID vendor "GSM", prod id 22142
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): Probing for EDID on I2C bus 2...
(II) NV(0):   ... none found
(EE) Kensington      Kensington Expert Mouse: Read error: No such device
(II) config/hal: removing device Kensington      Kensington Expert Mouse
(II) Kensington      Kensington Expert Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Kensington      Kensington Expert Mouse
(**) Kensington      Kensington Expert Mouse: always reports core events
(**) Kensington      Kensington Expert Mouse: Device: "/dev/input/event6"
(II) Kensington      Kensington Expert Mouse: Found 4 mouse buttons
(II) Kensington      Kensington Expert Mouse: Found x and y relative axes
(II) Kensington      Kensington Expert Mouse: Configuring as mouse
(**) Kensington      Kensington Expert Mouse: YAxisMapping: buttons 4 and 5
(**) Kensington      Kensington Expert Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Kensington      Kensington Expert Mouse" (type: MOUSE)
(**) Kensington      Kensington Expert Mouse: (accel) keeping acceleration scheme 1
(**) Kensington      Kensington Expert Mouse: (accel) filter chain progression: 2.00
(**) Kensington      Kensington Expert Mouse: (accel) filter stage 0: 20.00 ms
(**) Kensington      Kensington Expert Mouse: (accel) set acceleration profile 0
(II) NV(0): Probing for EDID on I2C bus 0...
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: GSM  Model: 567e  Serial#: 64804
(II) NV(0): Year: 2008  Week: 2
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 49  vert.: 32
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.635 redY: 0.342   greenX: 0.292 greenY: 0.611
(II) NV(0): blueX: 0.147 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): 1152x870@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Ranges: V min: 56 V max: 75 Hz, H min: 28 H max: 83 kHz, PixClock max 150 MHz
(II) NV(0): Monitor name: W2252
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff001e6d7e5624fd0000
(II) NV(0): 	02120103ea312078eaaec5a2574a9c25
(II) NV(0): 	125054a76b80950081808140714f0101
(II) NV(0): 	0101010101017c2e90a0601a1e403020
(II) NV(0): 	3600da281100001a21399030621a2740
(II) NV(0): 	68b03600da281100001c000000fd0038
(II) NV(0): 	4b1c530f000a202020202020000000fc
(II) NV(0): 	0057323235320a202020202020200044
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): EDID vendor "GSM", prod id 22142
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NV(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NV(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NV(0): EDID vendor "GSM", prod id 22142
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): Probing for EDID on I2C bus 2...
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus 0...
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: GSM  Model: 567e  Serial#: 64804
(II) NV(0): Year: 2008  Week: 2
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 49  vert.: 32
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.635 redY: 0.342   greenX: 0.292 greenY: 0.611
(II) NV(0): blueX: 0.147 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): 1152x870@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Ranges: V min: 56 V max: 75 Hz, H min: 28 H max: 83 kHz, PixClock max 150 MHz
(II) NV(0): Monitor name: W2252
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff001e6d7e5624fd0000
(II) NV(0): 	02120103ea312078eaaec5a2574a9c25
(II) NV(0): 	125054a76b80950081808140714f0101
(II) NV(0): 	0101010101017c2e90a0601a1e403020
(II) NV(0): 	3600da281100001a21399030621a2740
(II) NV(0): 	68b03600da281100001c000000fd0038
(II) NV(0): 	4b1c530f000a202020202020000000fc
(II) NV(0): 	0057323235320a202020202020200044
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): EDID vendor "GSM", prod id 22142
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NV(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NV(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NV(0): EDID vendor "GSM", prod id 22142
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): Probing for EDID on I2C bus 2...
(II) NV(0):   ... none found
```

I installed EnvyNG
sudo envyng -t
1. Install nvidia driver
0. 180.44-0ubuntu1 (Comaptable and Recommended)

EnvyNG Downloaded and installed the driver and prompted me to reboot.
I saved my file s and rebboted....
No Video, Monitor went into sleep mode, no response from system

Contents of /var/log/Xorg.0.log.old (The failed Boot)

```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux VBOXSVR 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul  3 17:56:31 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation GeForce 9500 GT rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000ef00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(WW) "dri2" will not be loaded unless you've specified it to be loaded elsewhere.
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded even though the default is to disable it.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Tue Mar 24 06:11:47 PST 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Tue Mar 24 05:51:43 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 9500 GT (G96) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 1048576 kBytes
(--) NVIDIA(0): VideoBIOS: 62.94.34.00.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 9500 GT at PCI:1:0:0:
(--) NVIDIA(0):     LG W2252 (DFP-0)
(--) NVIDIA(0): LG W2252 (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): LG W2252 (DFP-0): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) NVIDIA(0): DPI set to (87, 83); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
```

I hope this helps.. I am still learning Linux and troubleshooting things like this helps me learn more.

If there are any more commands I can enter into the Command Line please please let me know. I am also going to enter in the troubleshooting steps I have used in my BLog when I get the chance.

Thanks

Alex

---

### Post by Vasator on 2009-07-15
I am wondering if anyone in the community knows? 

I have 8GB of RAM installed on this System. Is there the possibility the kernel is somehow messed up with that much memory. The video card has 1GB of memory.

When I get home tonight I am going to swap out the memory and install the 2GB originally installed in the system and see if the video issues persist.

I found a forum somewhere (forgot to bookmark) where the issue was the video memory being mapped incorrectly causing this issue.

---

### Post by Vasator on 2009-07-15
Okay I got home and opened up my system. Took out the 8GB of memory and re-installed the 2GB of memory I had before. The issue is not with the card as I am currently running SL in the background and it is working perfectly!

There seems to be an issue with running the system with 8GB of RAM and if memory serves me right it is an issue with the kernel. I have read however that utilizing the 64-bit version of the kernel it should not be an issue. it however is.

---

### Post by Vasator on 2009-07-15
Confirmed:

I just re-installed the 8GB of memory
System froze upon bootup
Went into safe mode
ran xfix
up and running
no nvidia drivers working

This must be an issue with having over 4GB of memory and the kernel unable to allocate memory correctly.

---

### Post by Vasator on 2009-07-15
Okay after checking my notes and going through everything from the beginning I have resolved this issue. 

It was the BIOS.
I was running Version F6a
Latest Version was F9
I must have seen F9 and reversed the number in my head

Installed the latest BIOS and the system is running flawlessly now.

Sad thing is I must have checked the BIOS revision at least four times and my mind saw F9 when it was F6a all along.

---

### Post by dotduke on 2009-08-13
I'm having the same problems with 4 GB of RAM. Before I installed the AMD64 version I had a working 32bit version of Ubuntu 9.04 with NVIDIA 185 and VDPAU working.

Tonight I'll try to remove the 2 GB ram module and see if thats the problem.
Also will check the BIOS if there are any upgrades.

Thanks Vasator for all your hard work and not giving up! ;)

---

### Post by kellemes on 2009-08-14
> **dotduke said:**
> 
Thanks Vasator for all your hard work and not giving up! ;)

Indeed, thumbs up!
This became a very informative thread for others also..

---

### Post by dotduke on 2009-08-17
I took out the 2GB module of my Biostar TA690AG and restarted. After bootup it showed me the loging screen. After logging in my desktop. A quick check with NVidia Settings showed the right driver and GLX working.

Now it was time to update the BIOS to the latest version and try the system again with 4 GB of RAM.

It worked perfectly after updating the BIOS! I now have a fully functioning Jaunty 64 bit with NVidia restricted drivers.:P

---

### Post by Bluztrvler on 2009-09-10
Just found this thread.  I have been searching for a solution to this problem since 7.10. I've tried everything that I could find in the forums without success.  My symptoms are exactly the same, works well with the supplied driver, but when I install the restricted driver, the screen goes blank, and everything appears to be locked up.  I was blaming my ATI card, so I finally replaced it with a Nvidia 9600gs only to find the same result.  I am running an older Asus A8V 939 mobo, with only 2G memory in dual channel mode.  I haven't updated the bios in quite some time, and I am not even sure that Asus is still updating my boards bios, but that looks like a good place to start.

Thanks to all. I will post anything that I find, maybe it will be of help to someone else further down the line.

---

### Post by Bluztrvler on 2009-09-15
For what it is worth, I was able to get a bios update from 2005 for my 939 Asus motherboard, and it appears that this was the solution.  I have been limited on this computer for the last four years (my first Ubuntu was Breezy, 5.10) by this problem, and usually just ran the computer with Windows.  Ubuntu has progressed to the point now that it is practical to use Linux as the primary or only operating system for the majority of things that most folks use a computer for, and I am very pleased to be able to bring this computer into the Linux world.

Many thanks to the folks on this thread.

---

### Post by ifraser on 2009-09-20
Yes, I had the same problem with my Gigabyte GA-MA69GM-S2H with 4GB of RAM and flashing it to its most recent version (F6 as of posting time) solved the problem!  Thanks for being so diligent!  You have helped at least a few of us in the same boat.

---

### Post by edcompsci on 2009-11-27
Funny I have the same problem. I have:
Gigabyte iDNA GA-K8N51GMF-9 with AMD 64 (i think 3000+)
only 1.5 g ram
and I got a PCIe 9500gt card
got a new 21.5" widescreen monitor that has DVI and HDMI as well as VGA
I don't think the mouse has anything to do with it


and just like you, Jaunty loads a default VGA driver on it that works beautifully, while actually Vista Ultimate 64 gets stuck in low resolution mode.
I have tried seeing if unplugging the VGA connection would make the HDMI or DVI be detected and nothing happens. When I tried the recommended version 180 NVidia driver, I never got past a blank screen. I wonder if when I fresh install my Jaunty 9.04 (and by the way Jaunty has worked better for me than version 9.10 Karmic Koala) maybe I should not have a VGA plugged in and instead an HDMI or DVI cable, but that would be insane. Theere's no reason why I should have to do that.

Maybe we can help each other if we figure something out. Maybe the version 173 driver injtead of the 180.

---

### Post by IQRules on 2009-12-09
I have Nvidia FX1400 with 8.10 64-bit here.
I loaded with restricted 180 driver. Mine has issue with Samsung VGA wakeup. It just blanks, fails on wakeup.

So you guys out there, any issues on wakeup/standby?

---

### Post by IQRules on 2009-12-13
Finally, I fixed it the wakeup issue.

ubuntuHP:/var/log$ grep DPMS Xorg.0.log
(II) Loading extension DPMS
(II) NVIDIA(0): DPMS enabled

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection


I have 8GB memory with 8.10, FX1400, SATA raid in this.

---

