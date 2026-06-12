---
title: "Ubuntu 12.04LTS and Catalyst 12.4"
date: 2012-05-08
forum: Multimedia Software
---

### Post by Azyx on 2012-05-08
Have installed Ubuntu 12.04 with Catalyst 12.4 on a ASUS E45M1-M Pro (E450 AMD 1,6GHz dual-core and HD6320 gfx fusion(APU).I Have also installed XBMC. Movies, 720p mp4 works with a processor little over 50%. I'm not able to play BlueRay.ISO(CPU 100% and system load 3-4). The ISO-filese are on a USB 3.0-hdd, so there is not the 'bottle-neck. 
I wonder how I can fix this? I know nothing about different 2D accelerations and stuff. I have made 12.4-deb-files from a amd-'driver-installer-12-4-x86.x86_64.run' according to this:
[http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-in-12-04-lts](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-in-12-04-lts)

Installed the three deb-files.

Is something wrong or are the E450 and HD6320 not able to play BlueRay ISOs?

---

### Post by Azyx on 2012-05-12
I fixed by help from another tread and a page:
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Hardware_Video_Decode_Acceleration_.28EXPERIMENTAL.29](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Hardware_Video_Decode_Acceleration_.28EXPERIMENTAL.29)

When I installed [COLOR=RoyalBlue]**xvba-va-driver**[/COLOR] and [COLOR=RoyalBlue]**libva-egl1**[/COLOR], XBMC stop working, but in the limk above are PPA for a XBMC with support for hardware accelaration :)
Now it work fine with and my CPU eg APU in my case..do not overwork with h264 or Blue Ray ISO :)

/Cheers

---

### Post by ubik89 on 2012-06-19
One question:

Are you able to play 1080p HD stuff with vlc player and radeon hd 6320??

(because I'm not)

---

### Post by Azyx on 2012-06-19
> **ubik89 said:**
> One question:

Are you able to play 1080p HD stuff with vlc player and radeon hd 6320??

(because I'm not)

What kind of HD-stuff? I can not play blue ray iso (20-40GB movies) i  VLC, but with XBMC with XVBA (xvba is gfx-acceleration for ATI)

[http://ppa.launchpad.net/wsnipex/xbmc-xvba-eden/ubuntu](http://ppa.launchpad.net/wsnipex/xbmc-xvba-eden/ubuntu)

I  think It should be possible with VLC, but I think it lack some drivers,  but I don't know so much about it. (Computer says - it's not possible  to solve it)

 I don't have any other HD-stuff - 1080p  than this  iso:s. Other more compressed movies in 720p work with VLC, but It's look  better in XBMC....
The APU work at approximatly with 70%, both cases,  so the hardware are enoght for HD.

/Cheers

---

