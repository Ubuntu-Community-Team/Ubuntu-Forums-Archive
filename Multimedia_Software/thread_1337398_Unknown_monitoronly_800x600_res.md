---
title: "Unknown monitor/only 800x600 res"
date: 2009-11-25
forum: Multimedia Software
---

### Post by kwqd on 2009-11-25
I've seen several folks with this problem but the threads have become so convoluted with many responses, I can't keep them straight. My problem is:

I have installed both 9.04 and 9.10 (currently at 9.10) and have same problem. Highest resolution available is 800x600 and my monitor shows up as "unknown". This machine was originally an old Sears Lindows box that I have been using for email and word processing. There were several higher video resolutions available with Lindows.

Monitor: ACER AL1716

Video card:  01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266].

My video drivers seem to be current:

computer:~$ sudo apt-get install xserver-xorg-video-s3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-s3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 132 not upgraded.

computer:~$ sudo apt-get install xserver-xorg-video-savage
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-savage is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 132 not upgraded.

I have generated an xorg.conf file, but not tried to modify it, yet. 

Does anyone know how to fix this problem?

Thanks.

---

