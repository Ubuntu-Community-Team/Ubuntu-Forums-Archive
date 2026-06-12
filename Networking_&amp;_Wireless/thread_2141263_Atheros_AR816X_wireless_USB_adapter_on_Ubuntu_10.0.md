---
title: "Atheros AR816X wireless USB adapter on Ubuntu 10.04 LTS 64bit"
date: 2013-05-02
forum: Networking &amp; Wireless
---

### Post by galapogos on 2013-05-02
Hi,
I'm trying to get Ubuntu to detect my TP-Link WN722N wireless USB adapter which seems to be based on the Atheros AR816X, but I'm unable to do so. Are there drivers I need to install, and if so, where do I get them?

According to [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link) the adapter doesn't seem to be supported. Am I screwed?

Thanks!

---

### Post by chili555 on 2013-05-02
Please insert the device and open a terminal and run and post:```
lsusb
```> Ubuntu 10.04 LTS 64bitWe've made a lot of progress in drivers in three years. I strongly suggest you upgrade to 12.04 LTS.

---

### Post by galapogos on 2013-05-02
Hi,

lsusb shows the adapter as the following:

```

Bus 002 Device 005: ID 0cf3:9271 Atheros Communications, Inc

```

If it helps, I'm using the following kernel
3.2.0-030200-generic #201201042035 SMP

I'm using 10.04 LTS because I'm doing Android platform/OS development and that's the only officially supported version.

I've followed the instructions [here]("http://dwiel.net/blog/tp-link-tl-wn722n-on-ubuntu-10-04/"), except I've downloaded the compat-wireless 3.2 stable release instead(due to my kernel version), but I'm still failing at make with the following error:
```

compat-wireless-3.2.5-1/net/wireless/util.c:810: error: implicit declaration of function 'br_port_exists'

```

Any help would be appreciated.

Thanks!

---

### Post by galapogos on 2013-05-02
Quick update: I googled a bit more, and managed to find this [link](http://www.linuxquestions.org/questions/programming-9/compile-compat-wireless-921325/) that contained the solution. Applied the changes, and it built and installed perfectly. :)

Not sure why I had to make the changes though...

---

### Post by chili555 on 2013-05-02
> 3.2.0-030200-genericA Precise kernel? I believe it includes ath9k_htc and that all you'd need is firmware. Did you double-check?```
modinfo ath9k_htc
```Please post back if you need guidance in installing the firmware.

---

### Post by galapogos on 2013-05-03
I'd previously copied the firmware to the firmware directory but that didn't seem to work.

---

