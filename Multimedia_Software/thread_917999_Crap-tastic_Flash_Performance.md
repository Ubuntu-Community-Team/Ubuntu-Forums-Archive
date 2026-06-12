---
title: "Crap-tastic Flash Performance"
date: 2008-09-12
forum: Multimedia Software
---

### Post by pingnak on 2008-09-12
When I play Flash 9 applets in native Linux with Ubuntu 8.04, Nvidia, all up-to-date and stable, Flash is painfully slow compared to running Flash 9 in a virtual machine (VirtualBox) running Windows XP under the exact same Linux session where performance is bad.

For example, a reasonably complete Flash raycasting engine gets 12FPS under native Linux, and 48+FPS in a virtual machine running under the same session.  

Just to make this clear, in one browser session, Flash is slow, and in a window right next to that browser, on the same monitor, running a Windows virtual machine, Flash is fast.

It seems unlikely that this can be explained away with 'hardware acceleration', as virtual machines don't get much in the way of that, especially if you're going to blame a mal-configured PC.  If that were the case, I should get WORSE performance under the virtual machine session.

It looks to me like Adobe has given us a 'generic' build of the Flash plugin, without any of the 'just in time' compile features enabled for Intel, or we're building what we get with the wrong make flags so it'll build on 'any' platform, but doesn't take advantage of the Intel/AMD optimizations.

Manually installing an earlier 'Flash 9 r48' makes a vast improvement in performance, so that's going to be my little work-around for now.

The various earlier versions of Flash can be had here:
[http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip)

The ray-caster that exercises Flash 9 in this manner is here...
[http://hbrc.sourceforge.net/](http://hbrc.sourceforge.net/)

---

### Post by iBurger on 2009-04-13
thank you for sharing this. Flash is indeed faster in a virtualbox. (amazingly).

---

