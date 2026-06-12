---
title: "Skype video segmentation fault"
date: 2009-12-05
forum: Multimedia Software
---

### Post by jwaclawsky on 2009-12-05
I tried posting this on the "Dell Support" but I am not getting any "support" :-) maybe someone can help me in multimedia & video. My thoughts are that skype is outputting to X11 and I need to configure the system to use X11 with Skype but I can't find out where to set the system default to X11 for all my video, or should I be using something else? My detailed problem is: 

Skype was working fine on my Dell Mini 9 with Ubuntu 9.04 and then I installed the updates from the update manager yesterday (which I noticed included some skype updates) and then after that Skype crashes when I start my video. I thought there might be a problem in the update so I waited to see if a new update happens, and today I installed another set of updates hoping that would solve the problem (but I didn't notice any skype updates in it). I am not sure if the problem was due to the updates but I hadn't done anything else and that is the only skype change that I am aware of. I still have the problem. 

I have ran a test to my wife's windows XP machine (which always worked before). Another symptom is there is a very long delay in the voice from my computer (over 3 seconds of delay) to her XP machine but no delay from my wife's computer back to mine (we can hear each other speaking in the different rooms of my house so we can time the delay). Then when she starts her video or when I test skype video in the skype options menu the result is a repeating error. 

X Error, request 132, minor 18, error code 11 BadAlloc (insufficient resources for operation)
X Error, request 132, minor 18, error code 11 BadAlloc (insufficient resources for operation)
X Error, request 132, minor 18, error code 11 BadAlloc (insufficient resources for operation)
....etc.....

However, when I start my video on a call the repeating error stops and the skype crashes with a "segment fault" error message

X Error, request 132, minor 18, error code 11 BadAlloc (insufficient resources for operation) 
Segmentation fault

Can anyone tell me where I can find information on this error and error code. I would be grateful for any assistance. Thanks

---

### Post by Slade Winstone on 2009-12-12
Firstly, I'm not sure if this will help at all (YMMV), but here goes:

Specs:
- Running Jaunty 9.04
- Intel Graphics (laptop screen supports up to 1280x800)
- Skype 2.1 Beta (direct from the skype) for i386
- USB Logitech QuickCam Communicate STX webcam (gspca driver?)

FIRST PROBLEM:
==============

Apparently V4L (video drivers) have switched from version 1 to 2, or something like that, for that webcam chipset and you have to point them back to the older drivers to get Skype to work with the command:

$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

This command will load Skype with the appropriate V4L older compatibility drivers (ver 1).

SECOND PROBLEM:
===============

Now, when I ran up Skype in a terminal and tried to test the Video I got the error message:

"X Error, request 132, minor 18, error code 11 BadAlloc (insufficient resources for operation)"

This is actually an indication of a problem with video playback/the intel video drivers.

What I found was the for some strange reason the xorg.conf had some bad virtual display sizing (didn't put it there, and I would like to know what did!).

So, in /etc/X11/xorg.conf, the Screen Section had bad Virtual sizing:

<<BAD ENTRY>>

Section "Screen"
SubSection "Display"
Virtual 2304 800
EndSubSection
EndSection

<<CORRECTED ENTRY>>

Section "Screen"
SubSection "Display"
Virtual 1280 800
EndSubSection
EndSection

This corrected my problems and I can Skype with video now.

If you are still experiencing problems, try looking at your Intel graphics driver.

Hope that this helps you/somebody.

Slade.

---

