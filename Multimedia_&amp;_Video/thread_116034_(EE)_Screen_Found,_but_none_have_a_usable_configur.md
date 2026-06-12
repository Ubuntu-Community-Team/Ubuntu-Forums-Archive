---
title: "(EE) Screen Found, but none have a usable configuration"
date: 2006-01-11
forum: Multimedia &amp; Video
---

### Post by DragonX2 on 2006-01-11
Hey guys, a first time linux user here. 

I tried installing from the live CD, and everything worked great, but then xserver crashed, and it gave me the following error:

> PCI Mact64 in slot 1:0:0 could not be detected!
No devices detected

So I went into xorg.conf and changed the driver from ati to vesa, rebooted, and it worked perfectly. However, the resolutions were so horrible. The max was only 1024x768, so I tried manually editing the xorg file and putting in the resolutions I wanted myself in. However, that did not work as well. So I figured I had to install the correct drivers. I am on a laptop with an ATI mobility Radoen X700. So I went to the "How to" thread, about installing the ATI drivers, flgrx. I did it, but now, when I restarted, it tells me, "Screen found, but none have a usable configuration."

Now I am totally clueless about what to do. I tried running dkpg reconfigure xserver.. and tried changing the "best" resolution to just 1024x768, which was the previous config. Sadly, it did not work.

Any help would be greatly appreciated!

---

### Post by benny@linux on 2007-07-26
same problem here, what is the Graphic card you use?

---

