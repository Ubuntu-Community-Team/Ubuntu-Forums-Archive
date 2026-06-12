---
title: "network-manager applet shows Wireless 'unavailable'"
date: 2012-07-10
forum: Networking &amp; Wireless
---

### Post by bharath144 on 2012-07-10
While installing Ubuntu 12.04 LTS (server) on my Lenovo T60p, I selected the default interface to be Wireless and made it connect to my wifi connection. The installation went  well and I set everything up. The Wireless connnection was working fine until I rebooted my laptop. I observed that the network-manager applet shows Wireless status as unavailable.

The network connection gets disconnected quite often as well.

I looked around on the web and figured out a very inconvenient solution for this. The network went down everytime the laptop was rebooted or it went to sleep/standby/power saving mode. I had to run these to get the wireless (this happened to wired network as well) back up.

$sudo ifconfig wlan0 up

$sudo ifdown wlan0

$sudo ifup wlan0

This doesn't work sometimes too. It is proving to be impossible for me to use Ubuntu now.

Has anyone else faced this issue before? Is there a fix for this problem?

---

