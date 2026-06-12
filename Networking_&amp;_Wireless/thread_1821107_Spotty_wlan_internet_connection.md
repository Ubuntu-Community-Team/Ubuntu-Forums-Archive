---
title: "Spotty wlan internet connection"
date: 2011-08-08
forum: Networking &amp; Wireless
---

### Post by Persephone1 on 2011-08-08
Okay, I've been hunting like a madwoman to resolve this issue and I'd like to know whether or not there's something I can do about it. I have a dual-boot Windows 7/Ubuntu 11.04 system on a partitioned drive. When I use my Windows system (which is rare,) I have no problems connecting to the Internet. With my Natty system, I'll stay connected to the router, but that's about as far as it goes. My connection to the Internet is sporadic and I frequently have to reload pages and videos or restart downloads. 

This leads me to suspect the driver. I have a Realtek RTL8188CE chipset. Realtek was kind enough to issue a Windows driver but not a Mac or Linux driver. After some poking around, I found out that Ubuntu installs the RTL8192CE driver, which is also the version that can be downloaded from the Realtek website. I've also fiddled around with the MTU, but there's not a whole lot else that I'm finding at the moment. Is there anything I can do about this except to sigh loudly and hope that Realtek issues a better driver?

---

### Post by Persephone1 on 2011-09-02
Managed to get a workaround going. 

The main problem with the Realtek 8188CE is that the developers tried to COMPLY WITH ALL THE THINGS! Therefore, we got a chipset that was 801.1b/g/n mode compatible. I'm not going to go into what the difference between the modes are because you can just google that yourself. 

Unfortunately, developers for wireless routers have also been trying to comply with all said things and have developed routers that broadcast in b, g and n modes simultaneously. This is wonderful if you have a device that can only wireless over over, say, g, and your wife's computer can only do n. 

Because Realtek did a half-assed job on the drivers, not anticipating routers that broadcast over all three modes, they didn't bother to create a preference of one mode over the other. As a result, the chipset gets confused and constantly switches from one mode to the other. It'll connect but you'll constantly be getting DNS errors and having to refresh because the chipset is busy switching between modes at the same time as you're trying to load porn (or other wholesome internetty-activities) 

Realtek released an updated driver for Windows, but never bothered to update the Linux driver; possibly because they just gave us a driver that was cobbled together for a different chipset in the first place and didn't even think about updating that one. 

So here's the workaround. Log into your router ([http://192.168.1.1/](http://192.168.1.1/) or [http://192.168.0.1](http://192.168.0.1)) and under wireless settings, switch the 801.1 mode from b/g/n/ (or whatever the configuration happens to be) to /g/ only. This should solve most of the DNS lookup issues.

---

