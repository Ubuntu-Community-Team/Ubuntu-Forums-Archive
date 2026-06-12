---
title: "Wireless marked as &quot;Unmanaged&quot; in Network manager for no reason"
date: 2012-02-10
forum: Networking &amp; Wireless
---

### Post by andybeak on 2012-02-10
Hi,

I suspended to RAM and brought my laptop home.  When I got home my wireless connection in Network Manager was marked as "unmanaged" and I could not connect to my Wireless AP.

This problem seems similar to the one [here]("http://ubuntuforums.org/showthread.php?p=9402242") but that solution did not work.  In fact it has left two weird connections in my Network manager (labelled ifupdown).

I also tried to rm /var/lib/NetworkManager/NetworkManager.state and reboot (first tried to stop and restart the network manager service) to no avail.

cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

cat /etc/NetworkManager/NetworkManager.conf 
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true



I have recently used the pppoeconf command from the terminal, but the wireless was working after it.  All I did today was to "pon dsl-provider" to dial the modem.  

Could anybody give me an idea what these config files should read and how to fix this problem?

---

### Post by praseodym on 2012-02-10
Do you use a router (you do, right, because of wireless?!)? In this case remove anything but

```
auto lo
iface lo inet loopback
```

from the /etc/network/interfaces, remove the wired and wireless profiles from the NM and reboot.

---

