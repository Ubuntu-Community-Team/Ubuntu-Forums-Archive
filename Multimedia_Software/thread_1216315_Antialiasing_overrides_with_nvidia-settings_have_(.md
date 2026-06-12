---
title: "Antialiasing overrides with nvidia-settings have (almost) no effect"
date: 2009-07-18
forum: Multimedia Software
---

### Post by WindPower on 2009-07-18
Hi, I'm currently trying to get some decent antialiasing in Compiz and Wine. From what I've read, if you use an NVIDIA card (I have a [NVIDIA GeForce GT 120M]("http://www.notebookcheck.net/NVIDIA-GeForce-GT-120M.14953.0.html"), and have the same problem/results with a [NVIDIA GeForce 9800 GT]("http://www.nvidia.com/object/product_geforce_9800gt_us.html") on another computer), you have to use the Antialiasing setting panel and "Overrdide application settings", so that's what I did, but it seemed to have no effect. So here's what I did: I ran nvidia-settings as myself and as root user, and disabled all options in this panel (all to 0, and "Use application settings" for antialiasing), then restarted the X server. It looked like crap, as expected. See for yourself:
[[IMG]http://img269.imageshack.us/img269/8855/snapshot1dvf.th.png[/IMG]](http://img269.imageshack.us/i/snapshot1dvf.png/)

Now, I ran nvidia-settings as myself and as root again, and set it to "Override" and 16x, and I put Anisotropic Filtering to 16x as well, and I checked "Texture sharpening". I maxed everything out. Then I restarted the X server again. Now I can feel that it's much slower (cube is slow to rotate, lower FPS, and the fan got louder), so I suppose the antialiasing settings are in place... Only to see this:
[[IMG]http://img269.imageshack.us/img269/9260/snapshot2o.th.png[/IMG]](http://img269.imageshack.us/i/snapshot2o.png/)

Now don't get me wrong, it does look nicer (especially the cube's edge), but is that 16x antialiasing? It looks like blurry 2x antialiasing to me. Same result on the other computer with an NVIDIA Geforce 9800 GT. Using Kubuntu 9.04 64-bit on both, with the official binary nvidia driver, version 180.

So, is there something I'm doing wrong? First thing wrong I can think of is that I ran nvidia-settings each time as normal user and root user, while I suppose only one is necessary (which one?), but it shouldn't harm the graphics, should it?
Also, the antialiasing settings seem to have no effect in Wine (look at the Portal window, it looks the same in both screenshots). Is there something to configure, a registry tweak, something?

---

### Post by WindPower on 2009-11-15
Bump, still having this problem on another computer with NVIDIA GeForce 9600M GT, with drivers v190 (also happens with v180).

---

### Post by Sin@Sin-Sacrifice on 2009-11-15
[http://www.overclock.net/linux-unix/213952-how-advanced-wine-configuration-gaming.html](http://www.overclock.net/linux-unix/213952-how-advanced-wine-configuration-gaming.html) This may help with wine but I can see your point. Don't know how but when I set up my on-board 8200 correctly everything, literally, became much sharper. All I really changed was the amount of RAM wine sees the graphics card has. Everything in Ubuntu was much sharper when I started using the 185 drivers. I'm wondering if the 190 drivers would do anything more. As far as setting the desktop graphics manually... wish I could help more but I haven't had the privilege of using a good off-board graphics card since 2002. Hope the wine stuff helps. There are actually a lot of registry tweaks for performance in wine around the interwebs.

---

