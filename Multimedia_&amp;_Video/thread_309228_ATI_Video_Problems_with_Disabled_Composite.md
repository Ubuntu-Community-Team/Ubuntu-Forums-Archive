---
title: "ATI Video Problems with Disabled Composite"
date: 2006-11-29
forum: Multimedia &amp; Video
---

### Post by redwinedrummer on 2006-11-29
Hello guys!

I'm relatively new to the Linux world, I ventured into Ubuntu about more than a month ago. Having growing up as a Windows Baby, the transition wasn't all pretty, but nevertheless, I'm having fun with my new environment now.

I've managed to fix every problem I encounter with Ubuntu, thanks to the numberous guides and fixes online, however, I have given up on this one.

My installation experienced video problems a few days ago. Tearing of the interface, transparent terminal windows and Firefox not scrolling properly. I looked into it and figured that only updating was needed, so I followed the approach [here]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide"). It partially worked, though. I have already reistalled my *fglrx* drivers, but still experienced problems. I reconfigured xserver, and voila, a temporary fix. Unfortunately, my system reverted to the Vesa drivers, not the fglrx drivers.

My problem is, I am still experiencing the same video issue. I managed to isolate the problem and I found it to be the "Disabling Composite" step. Whenever I disable the composite option, my system detects my videocard and fglrx properly, but the problem still persists. Everything tears up, there are artifacts all over the screen during boot-up, log-in and restart/shutdown. Meanwhile, if I comment out that particular block, Ubuntu reverts to Vesa and my interface works fine. Now I'm stuck with Vesa drivers that cannot support 3D acceleration as efficiently as fglrx.

I hope anyone can help me on this. Any help is greatly appreciated!

If it helps anything, here are my specifications:
Intel Pentium 4 630
Intel D865GBF motherboard
Kingston 2GB DDR400
ATI X1600 Pro (AGP 512)
Creative Audigy 4

Thank you again!

---

### Post by Loco_gr on 2006-11-30
I have the same problem. I think it has to do with the specific ATI model X1600 Pro.

I am facing a problem with tvtime due to those drivers.
If there is anybody who might want to help here is the link:
[http://www.ubuntuforums.org/showthread.php?t=188967](http://www.ubuntuforums.org/showthread.php?t=188967)

---

