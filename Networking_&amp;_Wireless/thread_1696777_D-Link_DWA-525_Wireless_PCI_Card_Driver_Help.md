---
title: "D-Link DWA-525 Wireless PCI Card Driver Help"
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by SL6 Rules!!! on 2011-02-27
Hey,
I am relatively new to these forums and also to Linux. So my knowledge and especially ability to use the Linux Command line is relatively limited, going on 5 months in a week :D yay...!

Just for some background I have currently built a new desktop which is running running Scientific Linux 6 (64-Bit). However i am having issues with the newly installed PCI D-Link DWA-525 Wireless card (Bought Thursday of last week)

My current issue is that i have compiled and installed the linux driver rt2860 on the new system, but when i use the command line

>$ /sbin/insmod rt2860

It comes up with the no file or directory found. I have also looked into the directory for where the driver module should be (lib/modules/kernal_2.6.32.71.14.el6/net/wireless rt2860sta.ko). But the rt2860 & rt3060sta.ko module does not exist.

I am extremely frustrated because i have downloaded the required drivers from the ralink website & others (like fedora, fusion & centos) and read several forums to do with this driver, however none of the drivers contain this said module or install the rt2860sta.ko module onto my system. :(

I have even tried taking the file rt2860sta.ko module from the source.rpm and copying it directly to the kernal but this has not worked either.

I have a huge hunge that this is the direct cause for why i cannot gain wireless internet access. Thus i am at a huge loss as to what to do except go back to the store and ask for a refund or exchange for one that is known to work out of the box.

Any help would be greatly appreciated. As i have really limited internet access and desperatly need it for uni.

Regards SL6 Rules

---

