---
title: "issue with wireless adapter driver for BroadComm STA"
date: 2012-12-24
forum: Networking &amp; Wireless
---

### Post by priyadarshianu on 2012-12-24
Hi, I searched for hours on other threads b4 posting my question here. here it is - i installed ubuntu 12.04 along side XP. I can not see Enable Wireless option in networks button (top right) . i checked for solutions for hard/soft block with "rfkill list all", this is what i get " hp - wifi: hard blocked no ,soft blocked no". I checked for additional drivers and found broadComm STA for BCM43xx.( my wireless card is BroadComm BCM4311, found using "lshw -C network"). Activated the driver. But the 'configuration' for this device in 'lshw -C network' shows no driver. i restarted the system again and again. One interesting thing - when i remove the driver I get 'Enable wireless' as a disabled option along with (firmware not found), but when I activate the driver I get option whatsoever for wireless connections

---

### Post by Hadaka on 2012-12-24
Hi,please post

```
lspci -nn | grep AN 
```

Thanks

---

### Post by bkratz on 2012-12-24
> **priyadarshianu said:**
> Hi, I searched for hours on other threads b4 posting my question here. here it is - i installed ubuntu 12.04 along side XP. I can not see Enable Wireless option in networks button (top right) . i checked for solutions for hard/soft block with "rfkill list all", this is what i get " hp - wifi: hard blocked no ,soft blocked no". I checked for additional drivers and found broadComm STA for BCM43xx.( my wireless card is BroadComm BCM4311, found using "lshw -C network"). Activated the driver. But the 'configuration' for this device in 'lshw -C network' shows no driver. i restarted the system again and again. One interesting thing - when i remove the driver I get 'Enable wireless' as a disabled option along with (firmware not found), but when I activate the driver I get option whatsoever for wireless connections


The STA driver really doesn't work well with never Ubuntu versions and the BCM4311, you really need to remove it and install the b43 driver.  The following post should do both for you.

[http://ubuntuforums.org/showpost.php?p=12094989&postcount=12](http://ubuntuforums.org/showpost.php?p=12094989&postcount=12)

---

### Post by priyadarshianu on 2012-12-26
thanks for helping me out. I had some urgent work to do with my computer so I bypassed this problem n got the work done on Win XP. but sure will try out what u guys suggested. thanks again.

---

