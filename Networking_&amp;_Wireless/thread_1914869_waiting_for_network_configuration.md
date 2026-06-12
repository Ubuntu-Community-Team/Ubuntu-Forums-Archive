---
title: "waiting for network configuration"
date: 2012-01-25
forum: Networking &amp; Wireless
---

### Post by a.m.wink on 2012-01-25
Dear all,

After my upgrade to Oneiric, every reboot (luckily not that many) comes with the notification "waiting for network configuration" and then "waiting up to 60s ..." before continuing.

There are multiple threads about this already, I don't know which version of the problem applies to my case. I haven't found a solution that works for me.

It's not merely a warning -- networking does not come up automatically after rebooting.

However, if I just log in as root, do "ifdown -a" and "ifup -a", then (apart from a message of wireless not being configured), the wired network is connected again.

IOW, the configuration seems OK, but some startup script or other has become incompatible with the Oneiric setup.

In dmesg there are messages from modemmanager an dhclient/NetworkManager, but not very informative (the modemmanager ones shouldn't be there I guess?)

Does anyone know how to fix this? 

Best wishes
Alle Meije

---

### Post by Claus7 on 2012-01-25
Hello,

just a proposal: if you add those commands to your startup applications, maybe you are going to get rid of the problem.

Regards!

---

