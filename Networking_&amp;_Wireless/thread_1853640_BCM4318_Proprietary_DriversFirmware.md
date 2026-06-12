---
title: "BCM4318 Proprietary Drivers/Firmware"
date: 2011-10-02
forum: Networking &amp; Wireless
---

### Post by BrokenFishCake on 2011-10-02
I am using the b43 drivers, all seems fine, the B43 modules is running along with mac80211, no problem there. The problem lies with the firmware. I read that the updated b43 drivers only work on my card with firmware revision 4; i currently have revision 3.

I will add that this card ran perfectly until the drivers were updated.

I have tried but cannot find a resource for the proprietary drivers. yes I have Googled, believe me i have looked. Does anyone else use this family of cards? Where did you download the proprietary drivers from?


Thanks.

---

### Post by BrokenFishCake on 2011-10-03
bump

---

### Post by pdc on 2011-10-03
do give detailed information

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by BrokenFishCake on 2011-10-08
Well I have provided adequate information as I have come here with a specific question; I am looking for proprietary drivers, for my Broadcom chip, so i can extract the most recent firmware revision. Giving you my system info is unlikely to yield anything useful. The laptop is also physically located elsewhere. 

To reiterate, where can I find the Broadcom ('bcm4318') proprietary drivers?

Thanks.

---

### Post by nm_geo on 2011-10-08
Not knowing what version of Ubuntu you have installed does make some difference and we really like to see the pci numbers for your card.

Assuming you have Natty 11.04 installed not knowing you do.

You need the 

b43-fwcutter and firmware-b43-installer 


[B]Notes form Synaptic package manager on the firmware-b43-installer.
[/B]
> This package installs the firmware needed for usage of the b43 kernel
driver.

Supported chipsets:
 - BCM4306/3
 - BCM4311
 - BCM4312
 - BCM4318

---

### Post by BrokenFishCake on 2011-10-10
It appears that the card was switched off in the BIOS. Strange, it was working, I updated the system, rebooted and it had went into an off state. 

Sorry for wasting your time.

---

### Post by BrokenFishCake on 2011-10-10
Hmm, it appears that it is a bug with the 2.6.31 kernel; see here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/505821](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/505821)

Apparently it won't be fixed. This affects all BCM43XX chip revisions < 3.  If this affects you, you will just have to make do with switching your card on after a suspend, or find a way to block software from turning the card on and off in the BIOS.

---

