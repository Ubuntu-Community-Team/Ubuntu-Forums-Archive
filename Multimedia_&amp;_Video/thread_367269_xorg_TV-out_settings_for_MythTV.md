---
title: "xorg TV-out settings for MythTV"
date: 2007-02-21
forum: Multimedia &amp; Video
---

### Post by atomicfire on 2007-02-21
Using this guide:
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

and the latest Ubuntu desktop install CD, I was able to get my MythTV box up and running under an hour, including all system updates and such. This is the hardware in my computer:

Athenatech MicroATX case
ATI TV Wonder (old good version)
Pentium 4 2.0 Northwood
512MB RAM
80GB hard disk 

One thing to note, when I finish setting this up, all video will be stored on a 1.2TB network storage array instead of the dinky 80gb drive :)

Onboard ATI Radeon 9100 Pro graphics too - I know ATI is a pain in the *** to get it to work, but I want to see if I can get this to work on the spare hardware that I have without having to buy anything extra.

It all worked out of the box. Perfect too, if I might add. On a regular PC monitor at 1280x1024, TV is displayed exactly as it should be with all pause, record, plugins working great. I love it.

Only problem is when I switch to TV-out. I have a small 20" LCD TV here, with only Composite and S-Video inputs. When I plug either into the computer (it has Composite and S-Video outputs on it) and reboot, the BIOS and Ubuntu loading screen work fine, but as soon as it begins the autologin proccess and automatically start Mythfrontend, the display gets all scrambled and distorted, like my refresh rate is off. This happens with both the Composite and S-Video outputs - i've tried limiting my resolution to 1024x768, then 800x600 with no effect. The output is still scrambled.

I've come to the conclusion that my xorg.conf needs a little tweeking to get it to work right with the TV out because this problem occurs only when xorg is loaded. Anyone have experiecne with this?

-AtomicFire

EDIT:
searching reveiled something. I'm going change my monitor section to this to see if it works:

> Section "Monitor"
	Identifier	"TV"
	HorizSync	30-50
	VertRefresh	60
EndSection

---

### Post by barney_1 on 2007-02-22
I've had quite a bit of trouble with this myself.  You might check out this thread:

[http://ubuntuforums.org/showthread.php?t=249846](http://ubuntuforums.org/showthread.php?t=249846)

I have the TV-out working but I don't know how I can tweak the overscan so that the picture occupies the whole scree (there are narrow bands at top and bottom of the TV)

---

