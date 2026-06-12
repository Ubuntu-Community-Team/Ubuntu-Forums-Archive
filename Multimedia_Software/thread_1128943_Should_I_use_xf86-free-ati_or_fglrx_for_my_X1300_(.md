---
title: "Should I use xf86-free-ati or fglrx for my X1300 (r500)"
date: 2009-04-18
forum: Multimedia Software
---

### Post by Crandom on 2009-04-18
Well, I upgraded to 9.04 RC yesterday and noticed that I actually got graphics without installing fglrx, did some research and found out about this new open source xf86-video-ati driver that was running.

I know AMD will drop support for my card in Catalyst 9.5, so should I install fglrx or leave xf86-video-ati as it is? What are the performance figures and how do they differ?

---

### Post by steefjeqv on 2009-04-18
Hi,

The xorg-video-ati driver has better 2d quality (thats for sure).
On my Intrepid box I still need to disable composite for the moment. Otherwise i get "tearing"

The propriearity driver should yield more performance in the 3D section.

I've been using the xorg-video-ati driver for a while now (ever since 6.3 I believe) and it get's better and better + it runs stable.

In my opinion the free driver is better because it's stable and in constant development, compatible with new linux kernels, new xserver versions and so on..... .
Thanks to AMD (for providing the open source info and backup) and the driver developers this is the best open-source graphics driver around. 
You can even get new versions for Ubuntu through Tormod Volden's ppa.

Greetings,
Steven

---

