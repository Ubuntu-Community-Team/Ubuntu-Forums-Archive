---
title: "How to get Ubuntu to keep resolution"
date: 2006-07-14
forum: Multimedia &amp; Video
---

### Post by foots2015 on 2006-07-14
Hello I have recently got dapper set up on my laptop.

My laptop has intel graphics so i used the 915resolution hack to get my correct resolution. Problem is when dapper boots up resolution is low and i can't make it higher. But if I restart X by ctrl+alt+backspace, now the resolution is correct. How can I make it so the resolution is always set at the native resolution so I don't have to restart X every time i turn the computer back on?

---

### Post by ahaslam on 2006-07-14
What resoloution do you want?
What does your xorg.conf show under **Section "Screen"**?
The highest resoloution listed will be used if supported by hardware & driver.

Tony.

---

### Post by Six_Digits on 2007-11-06
Do you have the drivers for your video card?

If so, open your xorg.conf file like this:
```
sudo gedit /etc/X11/xorg.conf

```
Then change the resoloutions listed under "Modes" in the "Screens" section to what you need. 

For example-

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600 GTS]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection
```

Save, restart, and apply the resolution you want, should do the trick.

---

### Post by Qinjuehang on 2007-11-06
Oh and make sure the "Default" resolution you want, or the resolution you want it to start up with, is the first in the list.

---

### Post by Tony3286 on 2007-11-08
Qinjuehang

I am having problems with an "Out of Range" box showing at boot up with Gutsy and have been reading any post related to resolution. This out of range box appears at bootup , travels from left to right then my login appears and everything is fine. I notice you said in your last post to have the resolution you want as the first entry. The resolution I want is 1024X768. The problem is ONLY at bootup - once I'm logged in everything looks fine. My log shows:

Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Is it possible by changing the 1280x1024 with 1024x768 as the first entry this out of range
box will be corrected?

Tony

---

### Post by Six_Digits on 2007-11-17
Tony-
> I am having problems with an "Out of Range" box showing at boot up with Gutsy and have been reading any post related to resolution. This out of range box appears at bootup , travels from left to right then my login appears and everything is fine. I notice you said in your last post to have the resolution you want as the first entry. The resolution I want is 1024X768. The problem is ONLY at bootup - once I'm logged in everything looks fine. My log shows:

Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Is it possible by changing the 1280x1024 with 1024x768 as the first entry this out of range
box will be corrected?


You would actually have to do that to the LAST line because your default depth is 24, and I'm not even sure that would fix your problem. This box disappears when your desktop loads?

---

### Post by Six_Digits on 2007-11-23
Did this help at all?

---

