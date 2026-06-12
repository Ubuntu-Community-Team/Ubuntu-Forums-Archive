---
title: "Broadcom BCM4313 does not connect to one particular wifi net"
date: 2013-02-06
forum: Networking &amp; Wireless
---

### Post by jolubaes on 2013-02-06
My Dell laptop didn't have problems connecting to my wifi at home, now it just doesn't connect. I'm not sure, but probably it was after an update. It can see the wifi, it can connect to other wifi's without a problem. It can connect to my home wifi from windows. Other computer can connect to my home wifi. I can connect to my home network by wire. It just doesn't connect by wireless.

I have tried a couple of things, basically change the drivers, but no sucess yet.

I would appreciate any suggestion.

Thanks in advance

---

### Post by mörgæs on 2013-02-07
Please begin with a complete hardware description, especially of the network card(s).

---

### Post by jolubaes on 2013-02-07
Hopefully this is enough

  *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 1c:65:9d:31:91:f2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.2.0-37-generic-pae firmware=N/A ip=192.168.1.24 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:ff600000-ff603fff


04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

---

### Post by mörgæs on 2013-02-07
We'll find out. Now I have changed the title, hoping to attract an answer.

---

### Post by jolubaes on 2013-02-09
After a couple of weeks (and several fail trys) without doing anything (consciously) it start working again.

thanks anyway

---

