---
title: "Dell 1390 + Network Manager/WPA= No Wireless"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by tirofiban on 2006-06-18
Hello,
I have a Dell E1510 Inspiron with a Dell 1390 wireless card.

I followed the instructions on the thread: [wireless] Ubuntu 6.06 - Howto install BCM1390M as used in Dell D620.

NDISWRAPPER works great, I can see the wireless networks and hop onto my neighbor's unprotected wireless network with ease.

However, when I comment out everything but lo in the /etc/network/interfaces file and create wpa supplicant file with ENABLED=0, I have no wireless option. Knetwork manager shows only wired devices.

I rebooted, uninstalled, and reinstalled network manager, knetwork manager and WPA supplicant (via synaptic), and rebooted again. 

Any thoughts on why Network Manager can't see any wireless networks, but with the default Ubuntu networking  program, wifi works?

Is this some sort of bug?

Thanks in advance,
Marc

---

