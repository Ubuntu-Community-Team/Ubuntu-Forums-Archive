---
title: "s3 savage dri problem"
date: 2006-06-01
forum: Multimedia &amp; Video
---

### Post by Prinz Igor on 2006-06-01
hello folks,

with flight 7 opengl (with hardware acceleration) works fine! but now glxgears & co. are just killed every time.

there is a confirmed bug in launchpad.net but it seems to me that there does not happen anything. so i want to analyse the problem by myself. i hope you will support me.

i want to detect the modification that was made anytime after flight 7. please help me.

it is interesting that the driver package (xserver-xorg-driver-savage) does not change! so it must be another package - perhaps it is just a configure issue.

i have installed the old xserver-xorg-core (from flight 7) by copying the files out of the deb file to my root directory. it makes no difference. so perhaps this is not the package where the critical modification was made.

then i have tested glxgears with mesademos. i have detected that such programs chrash on functions like glCallList, glPopMatrix, glColor3f, ... which are reading the memory of the graphicscard. functions like glPushMatrix seem to work (do not crash).

i would be happy about every support, hints, ...

regards,

prinz igor

ps:

my graphicscard: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)

i have attached /var/log/Xorg.0.log and the output from glxinfo. i have not modified /etc/X11/xorg.conf.

i have a fresh installation - so the problem cannot be solved just with a new installation.

---

### Post by k7k0 on 2006-07-30
Hi, I have the same problem. Used DRI since breezy with no problems until this flight. ¿Do you found some workaround?

---

### Post by malathia on 2006-12-26
This probably won't help you, as it seems that your situation is different, but just in the off case that it does:

I had glxgears running smoothly (for a t22) since last flight for dapper. Noticing that I had erred and made my /boot partition too small to be able to test new kernels before switching to them, I decided to reinstall fresh. I loaded 2.6.15-27. When I went through my usual steps to get my savage card working with DRI.

As soon as I got DRI working, glxgears died. 

How I fixed this was I ended up going through my glxgears -info output, and saw that for whatever reason my savage card was being detected as AGP 1x, when it's 2x. You may want to ensure that your AGP slot speed is properly showing in glxgears -info, if it's not,

add:

Option "AGPMode"      "2" in the section of your video card driver in /etc/X11/xorg.conf and
Option "DMAMode"      "none"


This restored glxgears for me.

I'm just about to have shift transition at work, so I'll have to revisit this and actually make this post readable. But good luck.

---

### Post by malathia on 2006-12-26
Okay, so update to my last post... oddly enough, it worked for one boot and then went right back to doing this after a reboot. I'm still investigating. Will update if I find anything useful. I think it may be something with a combination of headers/image/ and drivers. Because I had removed the 26 headers after I got it working, and then poof.

Too soon to tell. But I'll get back to you.

---

### Post by malathia on 2006-12-30
I had the same symptoms after update. Refer to:

[http://www.ubuntuforums.org/showthread.php?t=326128](http://www.ubuntuforums.org/showthread.php?t=326128)

I solved it by forcing the BusType for my savage IX/MX to PCI.

---

