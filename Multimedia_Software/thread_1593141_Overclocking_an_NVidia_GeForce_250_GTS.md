---
title: "Overclocking an NVidia GeForce 250 GTS"
date: 2010-10-11
forum: Multimedia Software
---

### Post by ocirne94 on 2010-10-11
Hi all,
I was trying to overclock the graphics card you see in the title some time ago, with Kubuntu 10.04 and a can't-remember-which driver version; I was using NVclock because nvidia-settings didn't work at all for overclocking - resetting to defaults values on every click of "Apply" button. I managed to take the clock from 738 MHz to 800 and even higher, but some days ago I have upgraded to Kubuntu 10.10 and no overclocking works anymore: the clock frequency seems stuck on the default values. Driver 260.19.16 - any tips?
 Thanks
 Ocirne

---

### Post by NSDragon on 2010-10-14
This seems to be a recent bug on nvidia's part.

I have a 9600M GT and everything was fine in Lucid with the 256.53 driver (except in my case I underclock, to avoid semi-random severe slowdowns when my card decides it's too hot and throttles itself to cool down).

Maverick comes with the 260.19 beta driver, and while it works just fine, I found that it doesn't let me specify my own clock speeds; it'd just snap back to the default. The official driver just released yesterday (directly from nvidia, not from the Ubuntu repos) is the same. Curiously the GUI of nvidia-settings says it set my clock speeds to the default no matter what I choose, but from the terminal (with the -a switch) it shows me the speeds I chose, but with no actual effect.

Sadly, the 256 driver plays merry hell with Maverick's xorg 1.9, so I can't use it without xorg eating up a good chunk of CPU usage.

---

