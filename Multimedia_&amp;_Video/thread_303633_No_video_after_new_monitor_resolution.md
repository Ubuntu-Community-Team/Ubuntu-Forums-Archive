---
title: "No video after new monitor resolution"
date: 2006-11-20
forum: Multimedia &amp; Video
---

### Post by slick on 2006-11-20
I resently purchaced a new monitor that has a resolution of 1680x1050. My old resolution was maxed at 1240x1024 so I did the command suggested in the xconfig "sudo dpkg-reconfigure -phigh xserver-xorg", reboted and everything whent fine, until I tried playing video:mad: . When playing video (any player) it opens then you see a blue screen and closes. I suspect that I need to add the new resolution to the xconfig file, but same thing happens when I set the resolution back down. 

Any help would be appriciated... thanks.

---

### Post by nexes on 2006-11-26
No one has a solution to this?

I just recently upgraded from a 17" Samsung flat panel to a 22" widescreen and had to upgrade xserver to 1680x1050, and also lost the ability to play video.

It opens in MPlayer, flashes blue, then crashes a moment later.

---

### Post by nexes on 2006-11-27
Okay, it turns out to be a simple fix, at least on my end.

I wasn't thinking when I did the sudo dpkg-reconfigure xserver-xorg. That fixes the resolution, but reverted back to the nv driver. I had to run nvidia-xconfig again after applying the new resolution to restore the nVidia drivers.

Maybe that will help you as well? I feel kind of silly for not realizing my mistake sooner. It sounds like your situation may be a bit different, but it shouldn't hurt to run xconfig again just in case.

---

### Post by slick on 2006-11-30
I figured it out, my xorg.conf started using nv for drivers, so I reinstalled the newest driver from the nvidia site and now it seem to work. However I can only get the 1600x1024 resolution, and even though its close it looks like crap. This is mostly due to my video card (fx 5200), I tried my frends 7800gt and it worked at 1680x1060 but with some funky lines and screen shifted about 1/2 inch to the right, that is likely due to the driver set up was for my card. Anyway nvidia driver works nv driver does not, I have to use the nvidia X server utility to get the resolution it is not in my the system preferences, also FX 5200 does not support 1680x1050 under current nvidia driver.

---

