---
title: "TP-LINK TL-WN321G not working while Alternate CD Install."
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by AkifTariq on 2009-12-29
Hello Guys,
Normally I install Ubuntu from either Minimal Installer CD or Alternate Installer CD. Things went well yet, but then I had to switch from wired to wireless network. I have TP-LINK TL-WN321G wireless USB stick and Ubuntu finds my wireless network well on installed setup or live CD. But I want to Install Ubuntu from alternate CD or Minimal Installer CD but both cannot find its network. although they can list my TP-LINK TL-WN321G device while installation but cannot list Wireless Network. I also entered SSID by hand but no use. There is no security on my wireless network.

The question simply is that why my wireless network cannot be found when I boot from Alternate or Minimal CD to install Ubuntu, when they can be found very easily when I boot from Live CD.

The lsusb gives the following results in my case:

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Please help if I am missing something.

---

### Post by Project PWNED on 2010-01-07
I just installed the card yesterday and it works fine with me. Did you type: ifconfig wlan0 up

---

### Post by Alaadragonfire on 2010-09-12
hey i have the same adapter and when i installed ubuntu 10.4 it recognize the card and it says wireless connected but no internet access i checked everything and everything is fine and as it should be but i still cant access the internet please help

---

### Post by Elfy on 2010-09-12
> **Alaadragonfire said:**
> hey i have the same adapter and when i installed ubuntu 10.4 it recognize the card and it says wireless connected but no internet access i checked everything and everything is fine and as it should be but i still cant access the internet please help

Don't post and hijack someone elses thread and then repeat the information of a thread of your own.

---

