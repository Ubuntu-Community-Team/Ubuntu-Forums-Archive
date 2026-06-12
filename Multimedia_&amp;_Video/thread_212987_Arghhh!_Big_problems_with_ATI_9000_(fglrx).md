---
title: "Arghhh! Big problems with ATI 9000 (fglrx?)"
date: 2006-07-10
forum: Multimedia &amp; Video
---

### Post by fantosa on 2006-07-10
Hey,

I've tried installing the ATI drivers for my HP laptop using "Method 1" here:
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

When I restarted my computer the graphics were completely messed up so I reverted back to an old Xorg.conf.

Looking back through the page it appears that there is a problem with my specific laptop (HP NX7000)

> Beginning with ATI driver version 8.19, the drivers fail to properly detect modelines that are compatible with the LCD screen of the HP zt3000 (and equivalent Compaq nx7000 model), and they must be inserted into xorg.conf manually. For the 1680x1050 LCD screen, inserting the following modelines into the "Monitor" section works:

I inserted the modelines into the first monitor section (there is 2) and now I get a black screen (with faint stripes).

Anybody know how I can fix this? [-o< 

Thanks! :KS

P.S. I'm using Kubuntu

---

### Post by fantosa on 2006-07-10
I used gtf to generate a modeline for the monitor (1280x800 - 60Hz) and you can now easily decipher whats going on the screen but its still shaking all over the place.

Is there any way to find out what modeline is being used when the standard (non fglrx) driver is loaded?

---

