---
title: "Unable to move DSL from one linux machine to another"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by nyx14850 on 2011-01-02
Hi, I have a netbook running ubuntu 10.04 Lucid Lynx and it is connected to the internet using DSL high speed internet Comcast---standard coaxial cable to modem to ethernet cabel to my netbook. The wired connection is Auto eth0. It works fine. 

However, I have recently installed ubuntu 9.04 desktop edition on ANOTHER laptop and cannot get it to connect to the internet using this same modem and cable. When I plug in the ethernet cable it searches for wireless networks but won't recognise the wired network connection---Wired Network disconnected. Auto eth0 shows up under Network Connections and it has the MAC address and is set to connect automatically. I have tried restarting the computer and unplugging and plugging in the modem after about 15 min. Did not help. 

Anyone know why I cannot just move my comcast ethernet cable from one machine to another?

---

### Post by PatchesTheCaveman on 2011-01-02
Canonical stopped supporting Ubuntu 9.04 Jaunty Jackalope on October 23.  That means you can't download updates for it, and since it's so old it might not have the proper drivers for your Ethernet card.

If possible, you should consider updating to LTS 10.04 Lucid Lynx or 10.10 Maverick Meerkat.

---

### Post by nyx14850 on 2011-01-02
ok, i'll upgrade then. thanks.

---

