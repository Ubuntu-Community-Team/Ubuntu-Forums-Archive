---
title: "inconsistant speed using update manager and package manager"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by paintball9 on 2009-03-05
i recently decided to come back to ubuntu as an alternative to OSX86 and decided to do some updates today. anyways when i was doing the updates i noticed a very inconsistant download speed, ive attached a screenshot of the system monitor showing when it was working. it took me over 4 times the amount of time it should have taken to download the updates. im working from behind a proxy and i got that all set up. the proxy has a bandwidth throttler on it that limits me to around 60 Kilobytes per second on linux and 45 on windows (yet more proof of windows ineffiency). other downloads seem to work fine, i can max out the connection with firefox and as far as i can tell it is only the update system that is plagued by this. ive never had any problems like this on my previous install, it was always a consistant speed. i was doing the updates over the wired connection and i haven't gotten to test out the wireless yet, it was not operational after installation but it is detected now. any ideas as to what might be causing this?

if anyone is curious my specs are:
Dual-boot
Vista Home Premium 64-bit
Ubuntu 8.04 Hardy Heron 32-bit
Acer Aspire 5920G
Intel Core 2 Duo Processor T5750@2.00 Ghz, 667mhz fsb and 2mb L2 cache
4 Gb DDR2
Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)

---

### Post by Shpega on 2009-03-05
May sound obvious but check your repository in Synaptic, mine by default was to the Canadian main server which is VERY slow, you can change it to any one you like, there is an automatic ping tool that will find the fastest near you, or generally any of the schools (.edu) all have fast connections.

---

### Post by paintball9 on 2009-03-06
i didn't check that but next time i go in i will, that sounds right because i am in canada, i dont remember what i choose as localization settings when i installed so thanks for the help.

---

