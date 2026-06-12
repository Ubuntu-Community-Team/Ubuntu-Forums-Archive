---
title: "Xorg screen problems"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by rastakid on 2008-01-12
Hi all,

After using Linux on the desktop for about 5 years (and Ubuntu for about 2 years) without any problems at all I finally ran into the problem that has been bugging Linux for a long time now: external screen management.

I've recently bought an MSI Megabook S271 notebook which has an 12.1" screen. Now, this is great to work on while on the road, but when you use it for more than 1 hour your head just starts to hurt (well, mine does), especially since it's running on a high resolution for such a small screen (1280x800).

So, I tried using an external 17" TFT screen using the VGA output of the laptop while in the office or at home. It's been nothing but trouble. At first I wanted to stretch the desktop to the external screen but I soon let that slip. After messing with Xorg configs for hours (using the ATI proprietary driver, and without) I still couldn't get the image right.

What I want: whenever I plug in the external monitor I want it to display my desktop in 1280x1024 @ 75hz on the external screen. I do not need to have an stretched desktop so the laptop's display may go off (or blank). When I'm not connecting the external monitor I just want the normal 1280x800 resolution again.

Whatever I do I can't get it right until in the end I had to delete my xorg.conf to get any screen at all :( Strangely after rebooting I would get the 1280x800 screen back on my laptop without even having a xorg.conf in /etc/X11/ :S

Anyway, what's the best way to go about this? I tried it using the ATI Catalyst Control Centre and using the Screens and Graphics tool that came with Ubuntu 7.10 but I still can't figure it out. It hurts my heart to see Windows doing this right without any config modifications at all :(

Yours Sincerely,
A little-bit-disappointed Linux user

---

### Post by Zugzwang on 2008-01-16
Maybe this will help you:

[http://ubuntuforums.org/showthread.php?p=4146250]("http://ubuntuforums.org/showthread.php?p=4146250")

---

