---
title: "Mythfrontend Will Not Load - X Errors"
date: 2009-03-12
forum: Mythbuntu
---

### Post by brianafischer on 2009-03-12
I recently did an apt-get upgrade and mythfrontend will no longer load.  Displayed below is my sys info and the frontend log.  I have no idea how to troubleshoot this issue and would be grateful for any help.


```
$ uname -a
Linux toshiba-laptop 2.6.28-9-generic #31-Ubuntu SMP Wed Mar 11 15:43:58 UTC 2009 i686 GNU/Linux
```

```
$ lspci
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
09:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

```
$ mythfrontend
2009-03-12 14:56:48.812 Using runtime prefix = /usr
2009-03-12 14:56:49.428 XScreenSaver support enabled
2009-03-12 14:56:49.429 DPMS is active.
2009-03-12 14:56:49.437 Empty LocalHostName.
2009-03-12 14:56:49.438 Using localhost value of toshiba-laptop
2009-03-12 14:56:49.438 Testing network connectivity to 192.168.0.51
2009-03-12 14:56:49.694 New DB connection, total: 1
2009-03-12 14:56:49.791 Connected to database 'mythconverg' at host: 192.168.0.51
2009-03-12 14:56:49.807 Closing DB connection named 'DBManager0'
2009-03-12 14:56:49.809 Primary screen 0.
2009-03-12 14:56:49.842 Connected to database 'mythconverg' at host: 192.168.0.51
2009-03-12 14:56:49.844 Using screen 0, 1280x800 at 0,0
2009-03-12 14:56:49.895 New DB connection, total: 2
2009-03-12 14:56:49.913 Connected to database 'mythconverg' at host: 192.168.0.51
2009-03-12 14:56:49.922 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-03-12 14:56:49.922 Enabled verbose msgs:  important general
2009-03-12 14:56:52.293 Could not open settings file /home/toshiba/.mythtv/mysql.txt for writing
2009-03-12 14:56:52.314 No theme dir: /home/toshiba/.mythtv/themes/Mythbuntu-8.04-wide
2009-03-12 14:56:52.337 Primary screen 0.
2009-03-12 14:56:52.339 Using screen 0, 1280x800 at 0,0
2009-03-12 14:56:52.341 No theme dir: /home/toshiba/.mythtv/themes/Mythbuntu-8.04-wide
2009-03-12 14:56:52.341 Switching to wide mode (Mythbuntu-8.04-wide)
2009-03-12 14:56:52.534 Using the Qt painter
2009-03-12 14:56:52.535 JoystickMenuClient Error: Joystick disabled - Failed to read /home/toshiba/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-03-12 14:56:52.535 lirc_init failed for mythtv, see preceding messages
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x360000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x360000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x360000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x360000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x360000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x360000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x360000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x360000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x360000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x360000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x360000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  149
  Minor opcode:  4
  Resource id:  0x28
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3600027
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  8
  Resource id:  0x3600027
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3600027
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3600027
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3600027
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3600027
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3600027
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3600027
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  149
  Minor opcode:  4
  Resource id:  0x28
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x360002d
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  8
  Resource id:  0x360002d
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x360002d

```

---

### Post by rlowery on 2009-03-12
What you say it doesn't load.  Do you mean the UI starts up showing various colours blocks but no text is visible, as if the UI displays ok but fonts cannot be loaded?

That is the behaviour I am seeing on my backend server whenever I start mythtv-setup or mythfrontend and the errors in my log looks the same as yours.

Googling around, various people report success in solving these sorts of issues by either by
1) Installing the msttcorefonts package
2) running mythfrontend.real --reset
3) running mythfrontend.real -O ThemePainter=qt

Unfortunately none of these works for me.    I can access livetv, just nothing displays on the screen.

My other frontends work fine.  The only other thing that I can think of is that it is related to me running the intel driver with the NoAccel=true to stop known lockups with the 865 chipset on my backend

Hope this info helps your situation

Cheers

-Rob

---

### Post by brianafischer on 2009-03-12
Thanks for the tips.  I tried all three suggestions and saw the same behavior.  Attached are two screenshots of the issue.

---

### Post by rlowery on 2009-03-13
Yep, thats exactly what I'm seeing too.  Eventually if you wait a bit for it to finish caching themes, you can hit enter to Watch Live TV (first menu item) and you will hear sound, but no picture.

Just as a matter of interest what graphics driver are you using?

Please report back of you ever manage to solve this issue, this has had me stumped for a week or so

-Rob

---

### Post by rlowery on 2009-03-13
I think I have worked out the cause in my environment.

I am running my backend X server with "NoAccel" "true" due to [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/304871](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/304871)

On my working frontend I did the same and got the same bad behavior, so it seems myth requires DRI.  Try looking at your xorg logs to see if DRI is disabled

According to comments in the above bug, a new 2.6.3 intel driver package should be available soon that fixes the problem so I can re-enable DRI

-Rob

---

### Post by brianafischer on 2009-04-06
I'm not sure what in the following config file makes things work, but I now have a functional mythfrontend.

I got this xorg from: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/340152/comments/9]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/340152/comments/9")

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Radeon RC410"
	Driver		"radeon"
	Option         "AGPMode" "1"
	Option 	       "GARTSize" "64"
	Option 	       "DRI" "off"
	BusID		"PCI:1:5:0"
	Option          "DynamicClocks"  "on"   #This is for laptop users, it saves energy when in battery mode.
	Option          "XAANoOffscreenPixmaps"
	Option          "AccelMethod"    "XAA"  #either XAA or EXA. "XAA" is the default and safe choice

	Option          "EnablePageFlip" "true" #only works with accelmethod "XAA"
 #       Option          "TripleBuffer"   "true" #This *might* help if you use something like Beryl and have slow video playback.
	#additional
#	Option 		"UseFBDev" "true"
	Option "VideoOverlay" "on"
        Option "OpenGLOverlay" "off"

EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option          "DPMS"
	HorizSync 30-70
	VertRefresh 50-140
	#Device		"Radeon RC410"
	EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
#	Load		"dri"
 	Load		"extmod"
	#Load		"freetype"
	#Load		"v4l"
 	Load		"dbe"
 #	Load		"glx"
	Load		"int10"
	Load		"vbe"
	Load 		"ati"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Radeon RC410"
	Monitor    "Generic Monitor"
	DefaultDepth	24
EndSection

# Section "Screen"
# 	Identifier	"Default Screen"
# 	Monitor		"Configured Monitor"
# 	Device		"Configured Video Device"
	
##EndSection

#Section "ServerLayout"
#	Identifier	"Default Layout"
#	Screen 		"Default Screen"
#	Inputdevice	"Generic Keyboard"
#	Inputdevice	"Configured Mouse"
#	Inputdevice	"Synaptics Touchpad"
#EndSection
        
Section "ServerFlags"
        Option          "DontZap"               "false"
EndSection

Section "Extensions"
        Option "Composite" "on"
EndSection

Section "DRI"
        Mode 0666
EndSection

#Then check the "ServerLayout" 

```

---

### Post by brianafischer on 2009-04-15
Well, the latest update just broke everything.  It looks like I am not the only one with this issue:

[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/341898/]("https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/341898/")

The DRI line is not making mythfrontend operational as a work-around either.

---

### Post by jk-menifee on 2009-05-03
Just wanted to report that this workaround from Bug 341898

```
For a workaround for now, can you please launch mythfrontend like this:

XLIB_SKIP_ARGB_VISUALS="1" mythfrontend
```

works for me.

John K.

---

### Post by usererror on 2009-05-26
The post above mine got it working for me, as well!

---

### Post by Macus on 2009-09-23
WORKS FOR ME TOO!
thanks.

Iv been spending ages trying to getting my thinkpad T42 working
(with mobility RADEON 7500)

is there some way to make this command execute at startup (and on the apps menu)?

---

### Post by klc5555 on 2009-09-23
> **Macus said:**
> WORKS FOR ME TOO!
thanks.

Iv been spending ages trying to getting my thinkpad T42 working
(with mobility RADEON 7500)

is there some way to make this command execute at startup (and on the apps menu)?

Rename the current /usr/bin/mythfrontend to /usr/bin/mythfrontend.old

Use an editor; compose a 1-line shell script. It contains the line:

XLIB_SKIP_ARGB_VISUALS="1" mythfrontend.old

Name this script "mythfrontend". Make it executable and put it in /usr/bin

Now, at X-start, when Mythbuntu's "mythfrontend.re" invokes "mythfrontend", it comes up with the correct parameters.

---

### Post by carchaias on 2011-07-31
#8 works for me too, but this works not for Radeon cards only. I've a nvidia GT210 wich stopped showing me TV pictures from my mythtv box some time ago (Why? No idea.) and with this it's back.

---

### Post by carchaias on 2011-08-06
There is a problem with the script. It is overwritten with the original file while the next update.

---

