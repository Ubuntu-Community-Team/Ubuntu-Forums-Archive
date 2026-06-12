---
title: "Verifying (and installing) mac80211 in 8.04"
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by UrBob on 2010-03-01
Firstly, I am reasonably technical but new to Linux. I almost guarantee there will be simple things that I don't understand. Thanks for your patience.
 
I am trying to get a USB wireless adaptor working with aircrack-ng and have managed to find that I should have the mac80211 drivers installed and active to support the rtl8187L and B chips. (I also need to patch them apparently, but first things first:)).
 
I am working with Ubuntu 8.04LT (I am fairly sure) and do not seem at the moment to be able to update to a more recent version on the target machine. The kernel is 2.6.24-27.
 
I followed instructions to blacklist the r8187 and ieee80211 modules, which seemed to go quite smoothly.
 
I now need to get the mac80211 module loaded, but can't find out how. The information at Aircrack-ng and related sites seems to indicate that I expect the drivers to be already in my build of Ubuntu but they do not seem to be loading. The suggestion seems to be that they will load automatically. I have found some stuff in /lib/modules/2.6.22-14 and /lib/modules/2.6.22-27, and also in /usr/src/linux-headers-2.6.24-27 which is probably relevant but I don't know what if anything to do with it.
 
If anyone needs more detailed information, just tell me what you need to know, and how to get it.
 
Thanks

---

### Post by UrBob on 2010-03-02
OK so no replies.
 
Lots has changed since I posted this.
 
Firstly, I found out that the reason I couldn't install Ubuntu 9.10 was a faulty CD Drive. (Didn't get any relevant errors just a comment that no suitable kernel was available to perform the install after the install environment loaded, from CD:confused:).
 
Secondly I found that the mac80211 support is apparently not useful in 8.04 and earlier, so a good thing that I managed to install 9.10.
 
Now I have at least one USB wireless adapter working just fine for normal networking and just have to figure out why it doesn't work at all for the aircrack-ng injection test. I think I have to patch the driver, but can't quite seem to find out how. Also there are at possibly three patches depending on version but I don't know if it's the kernel version or some other version.
 
If anyone does happen to have any information I would be interested, but I consider this thread closed.

---

