---
title: "Efficiency of networkmanager + wpa_supplicant + ndiswrapper"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by roland_mai on 2010-03-03
Hello,

I am posting here to get some opinions of what people think of the state of networkmanager + wpa_supplicant + ndiswrapper for laptops.
I have used Ubuntu for a while on my laptop and only recently switched to Gentoo. However, since this is a larger forum, I figured people might have greater insight, since the issue spans all distributions.

My major concern is the speed at which an IP is gotten using such a setup. I have my home router configured with WPA Personal (not v2) and often when I bring the laptop from standby, network manager will prompt me 3-4 times to enter my wireless password before getting an IP. This annoys me a lot. Often I won't even get an IP. Rebooting the router (WRT160Nv2) helps sometimes, but not always. I haven't seen such issues with windows. On my win 7 boot partition (yeah, I have one cause I can't run Adobe CS4 otherwise, and VM performance sucks), resuming from standby makes the computer associate and get an IP in a matter of seconds.

Does anyone have a clue why on earth it takes so much longer for ubuntu/linux setup to get an IP after standby? How does windows do the quick association + dhcp lease request? It doesn't seem like it goes through the same long process of associating at all. Why doesn't wpa_supplicant do something similar?

Thanks,

Roland

---

### Post by iponeverything on 2010-03-03
I think it probably an ndiswrapper issue. 

What is network the card?

---

### Post by roland_mai on 2010-03-03
It's a Broadcom card. I use bcwl5 driver that Lenovo distributes. In ubuntu both the broadcom-sta and ndiswrapper worked, but behaved pretty much the same way.

---

