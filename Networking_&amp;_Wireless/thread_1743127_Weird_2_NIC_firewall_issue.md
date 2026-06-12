---
title: "Weird 2 NIC firewall issue"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2011-04-29
Setup is 9:10 with eth0 (192.168.1.0/24 network) going to internet - works fine.

wlan0 (192.168.2/0/24) is connected, and seems to work fine. This will be for internal use, so in the Network Manager panel, I checked "only allow access to internal network" settings.

I use firestarter, and have added a rule to allow all connections from 192.168.2.0/24. I already have a rule 192.168.1.0/24 which works fine.

However, when I try to access the machine from the 192.168.2.x network, no joy, unless I stop the firewall. At which point it all works fine. However, Firestarter isn't flagging any events showing it's blocked any connections from that source.

Can anyone suggest what's blocking the connections, and why, and (of course) how to fix it ?

---

