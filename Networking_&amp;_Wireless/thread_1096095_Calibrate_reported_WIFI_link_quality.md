---
title: "Calibrate reported WIFI link quality"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by Calimo on 2009-03-14
Hello,

I have a PC with an asus M2N DH motherboard and an integrated WIFI chipset (Realtek 8187L). Kernel module used is rtl8187. It works fine (except some disconnections requiring a module reload with modprobe, but this isn't my question here).

When I used Hardy 32bits, the wifi signal quality reported by the Network Manager applet was between 60 and 90%.
Since I moved to Intrepid 64bits, it shows a stable but low signal power of 15%. See image :
[img]http://img88.imageshack.us/img88/7861/wifinmappletvt6.png[/img]

However, the connection seems to work equally well. I should note that my PC is very close (5 meters) to the wireless router, so 15% signal seems unrealistic (and very pessimistic).

Here is the output of wavemon.
[[IMG]http://img440.imageshack.us/img440/3222/wavemon.png[/IMG]](http://img440.imageshack.us/my.php?image=wavemon.png)
Link quality is usually 15/100, with short drops to 14 or rises to 16.
Signal level is very stable at 65 dBn. Noise level varies quickly between 10 and 40 dBn, usually around 20 dBn as in the capture. signal-to-noise adapts accordingly.

My question is: is it possible to calibrate the something somewhere to get NM applet report a signal power closer to the reality? If yes, how?

Thanks for your ideas !
Xavier

---

