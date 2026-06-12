---
title: "720P Video Playback ATI X200"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by cro_crx on 2007-10-20
Hey guys, just came back to Ubuntu this week, installed 7.10 on my laptop, coming from XP, and it's working great. I've ran into a bit of a problem though. When I'm watching video, when the video cuts very quickly the screen appears to tear, like the tearing you'd get without any Vsync, but for some reason it's cut across from the top right of the screen to the bottom left diagonally which is a bit wired, when i pause it the line isn't actually there.

Also I can't seem to play any 720P Video smoothly, i can watch normal rips in 640x352 on any video player, but when watching my 720p MKV rips (AC3 Audio) The video lags a fair bit, i tried using the basic movie player and VLC, VLC seems almost smooth, but lags in certain places, I actually copied the video to my laptop so it's not a streaming issue or anything, the CPU is at 100% when decoding so i rekon the video's just at it's peak, i'm running fglrx on my X200 video.

Is there any tweaks that can be done to my xorg config or is there another player that would decode faster or any tweaks to VLC i could do ( I haven't changed VLC config at all). I would hate to have to dual boot XP just to play HD video :S

The important parts of my xorg.conf

> # xorg.conf (xorg X Window System server configuration file)

Section "Device"
	Identifier	"ATI Technologies Inc RC410 [Radeon Xpress 200M]"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
	Option 		"VideoOverlay"		"on"
	Option 		"OpenGLOverlay" 	"off" 
	Option 		"EnablePageFlip" 	"True"
	Option 		"DRI" 			"true"
	Option 		"EnableDepthMoves" 	"true"
	Option 		"AccelMethod" 		"XAA"
	Option 		"NoAccel" 		"False"
	Option 		"XAANoOffscreenPixmaps"
	Option 		"ColorTiling" 		"on"
	Option 		"RenderAccel" 		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RC410 [Radeon Xpress 200M]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection
Section "Module"
	Load		"glx"
EndSection

Section "DRI"
	Mode	0666
EndSection

All those options in my xorg didn't seem to help much, I'm still getting 1660 in glxgears with the window actually showing.

My fglrx output:

> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)



I'm also running Compiz-fusion with the effects on, I've tried turning them off but still the same result. I did install XGL-Server(or whatever it's called), unsure of this matters or not (I was reading that it reduced video/gaming performance)
Any help or suggestions would be greatly appreciated. I don't mind testing things and i can supply you without any outputs that you think might help out.

Thanks in advance.

---

### Post by cro_crx on 2007-10-20
UPDATE ::

Ok just disabled XServer-XGL by adding a blank file here  --> ~/.config/xserver-xgl/disable
Seems to have worked, although now my video keeps jumping up and down like 1-2 times per second. I can tell its not stuttering anymore though coz the audio doesn't seem to be skipping, also the CPU usage seems to have dropped below 100%. I tried watching another video AVI Container (XVID) and it didn't jump up and down at all, tried another mkv i had and it's jumping, tried two different players as well (VLC and Movie Player).

Anyone have any ideas ?? I'm about to step out, should be back in a few hours.

---

