---
title: "Installed 10.04 and Lost wireless connection  right after updates"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by tehno 2 on 2010-06-06
I installed a clean installation of ubuntu 10.04 inside Windows 7 and wireless worked normally in the beginning that I downloaded and installed all the updates "I selected without updating Grub".
On the first reboot after updates, the wireless icon disappeared from the panel and could not connect to the internet although the settings in the Networking tools were correct.
Can someone help me please???

---

### Post by pedro_orange on 2010-06-06
Is the network card acknowledged by Ubuntu? 

```
lspci, lsmod, dmesg, ifconfig /etc/network/interfaces iwconfig
```

etc

This is a great page to check that will help you find out where the problem is: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

