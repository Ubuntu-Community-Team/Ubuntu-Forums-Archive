---
title: "clean start with wireless config"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by jcastilow on 2010-04-30
Hi,

I had put in a broadcom 4318 (airforce) card and it showed up in network tools as wlan6 with multicast disabled, inactive, and etc. the bf cutter tool also showed up in hardware drivers.

However, after trying to get the card functional - it no longer shows up in network tools nor is bf cutter in the hardware section.

I tried installing broadcom's proprietary driver among some other solutions. I'm running karmic 9.10.

Any suggestions on how to start with a clean slate and get my wlan6 to appear again, so I can install this proprietary driver or use driverloader? 

Thanks,

---

### Post by NichoTL on 2010-04-30
Usually the 'wlan6' interface is a result of the driver doing at least some of its job. If you don't have a driver the system might not assign an interface to the card. So I'm guessing that when you had wlan6 with the card showing in network tools, a driver was handling the card already (maybe a built-in driver). Is this a PCI card you are talking about?
if so can you run lspci in a command window?

---

### Post by bkratz on 2010-04-30
> **jcastilow said:**
> Hi,

I had put in a broadcom 4318 (airforce) card and it showed up in network tools as wlan6 with multicast disabled, inactive, and etc. the bf cutter tool also showed up in hardware drivers.

However, after trying to get the card functional - it no longer shows up in network tools nor is bf cutter in the hardware section.

I tried installing broadcom's proprietary driver among some other solutions. I'm running karmic 9.10.

Any suggestions on how to start with a clean slate and get my wlan6 to appear again, so I can install this proprietary driver or use driverloader? 

Thanks,

Well, if you have tried multiple drivers (b43,wl) you could have conflicting modules loaded-resulting in nothing good. you might want to post the outputs of

```
lsmod
sudo lshw -C network
```

(that is LSMOD and LSHW in lowercase, C in upper) so we can see what happened.

---

