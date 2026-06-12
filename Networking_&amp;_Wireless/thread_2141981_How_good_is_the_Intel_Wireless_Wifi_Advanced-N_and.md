---
title: "How good is the Intel Wireless Wifi Advanced-N and Ultimate -N"
date: 2013-05-04
forum: Networking &amp; Wireless
---

### Post by Microrobot on 2013-05-04
Does anyone own one, or have experience with one? I am thinking of getting one for my laptop.

---

### Post by kurt18947 on 2013-05-04
> **Microrobot said:**
> Does anyone own one, or have experience with one? I am thinking of getting one for my laptop.

[http://ubuntuforums.org/showthread.php?t=1978457&highlight=intel+advanced+N%2C+ultimate](http://ubuntuforums.org/showthread.php?t=1978457&highlight=intel+advanced+N%2C+ultimate)

This thread talks about the only problem I hear about with the Intel adapters.

---

### Post by chili555 on 2013-05-04
A subject near and dear to my heart. I have:> Intel Corporation Centrino Advanced-N 6200It and all similar devices after 4965, use the driver iwlwifi which usually works perfectly. They load firmware appropriate to the individual chipset:> $ modinfo iwlwifi
filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2012 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-3160-6.ucode
firmware:       iwlwifi-7260-6.ucode
The driver and firmware are built in to recent versions of Ubuntu by default.

Some device and router combinations work perfectly with 802.11N and use the 5 gHz band without any problems, including mine. However, in many other cases, the card, driver and router combination refuse to pass traffic unless N is disabled. A search of this forum for '11n_disable=1' will provide many examples.

I wish I knew the circumstances that differentiate working perfectly from not working unless N is disabled. I had thought that when I finally got an N router, I'd have plenty of trouble to work on; however, my system worked perfectly out of the box.

So, my answer is these cards always work, albeit perhaps without N.

EDIT: This may be a clue: [http://communities.intel.com/thread/40405](http://communities.intel.com/thread/40405)> Intel WiFi Products: Data rate will not exceed 54 Mbps when WEP or TKIP encryption is configured.I wonder if many 11n_disable issues are WEP or TKIP; set because other legacy devices on the network don't support PSK.

---

### Post by Microrobot on 2013-05-04
Thanks, this was very useful. I might go with Ultimate -N. I am a personal fan of Intel.

---

### Post by ahallubuntu on 2013-05-04
~

---

