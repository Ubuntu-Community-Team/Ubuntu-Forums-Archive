---
title: "Problem with Radeon 9600 Pro 3D Graphics on AMD64 with Ubuntu 6.06 Dapper 64bit"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by mtn on 2006-06-09
Hi,

I'm trying to get 3D graphics to work with my AMD64 and Radeon 9600 Pro, AGP x8 ATI graphics card. running Ubuntu 6.06 Dapper 64bit . I followed this how to...

EDIT: Solved (sorta) [see here]("http://www.ubuntuforums.org/showthread.php?p=1443388#post1443388").

[https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI](https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI)

All seemed to go well but the final check to see if it was working using the command  fglrxinfo produced errors...

mike@mike-desktop:~$ fglrxinfo
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18

Just in case it helps I have posted my xorg.conf below. Any idea? I'm a total noob by the way! (should that be with one “o”!


Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

---

### Post by kolach on 2006-08-17
Hi, I have exectly the same with my Mobility Radeon X700.
I see you asked for help long ago.
Did you solve it?

---

### Post by mtn on 2006-08-30
No...sorry. Just returning to this now. Going to give it another go. Will post if any luck!

EDIT: Well, have tried another bunch of "how tos" with out any luck. I'm thinking it might be worth reverting back to Dapper 32bit! Not really sure if that would help but thinking maybe the support for 64bit is not that good or somthing. Also wondering if all the messing about I have done now it getting in the way of things working.

I will post back here if I have any luck in the future.

---

### Post by mtn on 2006-08-31
Well, I have Radeaon 9600 Pro working with 3D support. I had to uninstall Dapper 64bit and install 32bit, I have not noticed any speed reductoin between versions, tho I'm guessing things like movie encoding will be slower!. Here is the post where I outline how I did got 3D working ...[http://www.ubuntuforums.org/showthr...]("http://www.ubuntuforums.org/showthread.php?p=1443388#post1443388")

---

