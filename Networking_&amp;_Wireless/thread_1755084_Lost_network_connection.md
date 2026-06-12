---
title: "Lost network connection"
date: 2011-05-10
forum: Networking &amp; Wireless
---

### Post by Pondoro on 2011-05-10
My PCdual boots Ubuntu and Windows XP. Both talked to my LAN beautifully. I updated Windows and Ubuntu stopped talking to the network. 

I'm thinking my network card got turned off in Ubuntu or my network password got wiped out of wherever I stored it. 

I cannot find where I tell Ubuntu, "This is my network password." I must have set it up months ago but I cannot find it now.

Windows still hits the network, by the way...

Any suggestions?

Thanks!

---

### Post by garvinrick4 on 2011-05-10
Post results of :
```
sudo lshw -C network
```

---

### Post by Pondoro on 2011-05-10
> **garvinrick4 said:**
> Post results of :
```
sudo lshw -C network
```

*-network DISABLED      

       description: Ethernet interface

       product: RTL-8139/8139C/8139C+

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 2

       bus info: pci@0000:02:02.0

       logical name: eth0

       version: 10

       serial: 00:16:76:5d:80:b7

       size: 100MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s

       resources: irq:21 ioport:1000(size=256) memory:80010000-800100ff

mike@Aethelred:~$

---

### Post by garvinrick4 on 2011-05-10
Right click on network applet and check enable.

---

### Post by garvinrick4 on 2011-05-10
If previos did not do it what does this say: run in a terminal:
```
gedit /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by Pondoro on 2011-05-10
> **garvinrick4 said:**
> Right click on network applet and check enable.

That worked, Thanks!!!

---

