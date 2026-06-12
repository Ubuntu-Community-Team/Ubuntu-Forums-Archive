---
title: "OMG, ATI TVout (I need someone who knows xorg.conf  to help me pleeeease :-) )"
date: 2009-10-26
forum: Multimedia Software
---

### Post by DexterLB on 2009-10-26
So.
I had an ancient NVidia MX-440 video card with an S-Video output. An output I used quite a pretty lot. I had nvidia-glx-96 proprietrary driver. Compiz worked almost like a charm, just a bit slow. My S-Video output was configured as a seperate X screen. (I used nvidia-settings)

So far so good. But, as I am stupid, I exchanged my old&working NVidia with a supernew superfast ATI Radeon 9600xt
So, I removed the NVidia driver and used EnvyNG to install the ATI driver which rendered X unusable. So I dropped to TTY, removed the ATI fglrx driver and did ```
sudo dpkg-reconfigure xserver-xorg
```, so the screen was reset to "Configured Monitor" or something, I'll post the actual xorg.conf later.
Anyway, after that the primary DVI monitor works properly and compiz has full and fast functionality ( I can't understand why, my proprietrary driver isn't installed #-o ). And if on startup I unplug the DVI monitor the videocard takes the S-Video as primary and I know the S-Video hardware works, as I can see everything on the telly.

So, now the actuak question: How do I configure the S-Video output to be a second X screen, virtually positioned to the right of the primary? How should I modify xorg.conf?

---

