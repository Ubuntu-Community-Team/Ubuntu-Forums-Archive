---
title: "modeline and resolution help"
date: 2009-05-28
forum: Multimedia Software
---

### Post by bigbudz on 2009-05-28
Hi, Im trying to get a new monitor working, but the resolution i need (1920x1080) is not available. The highest available is the resolution of my old monitor. (1280x1024) I am running Ubuntu 8.10 and nvidia GeForce 5200 vid card. I tried; 

1. sudo nvidia-settings. Highest res available was 1280x1024. 

2. Fresh install. The non-proprietry driver displayed 1920x1080 fine, but after installing the nvidia 173 driver that resolution wasn't available. 

3. Editing /etc/X11/xorg.conf  I added the Modeline line in the screen Section and the Display SubSection in the Monitor section. (Got the Modeline from the command gtf 1920 1080 60) This didn't change anything at all. Here's my xorg.conf
------------------------------------------------------------------------
Section "Monitor"
	Identifier	"Configured Monitor"
	Modeline "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"1920x1080_60.00"
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
EndSection
----------------------------------------------------------------------

I thought that would work for sure, but unfortunately it didn't. Any help sure would be appreciated.

---

### Post by bigbudz on 2009-05-28
Resolution fixed. Need to change frequency. 

after the command 'lspci | grep VGA' I realized that my video controller is VGA compatible and here I am using a DVI cable. When I used a VGA cable a whole new set of correct resolutions appeared with and without my modified xorg.conf. 

It is coming through at 50Hz and I need 60Hz so I will have to edit xorg.conf after all. I wonder if the res will be right if I use a DVI cable now?

Just need to get that frequency changed and possibly change the horizontal and vertical frequency as well b/c the display does not look the greatest now. Can anyone help?

---

