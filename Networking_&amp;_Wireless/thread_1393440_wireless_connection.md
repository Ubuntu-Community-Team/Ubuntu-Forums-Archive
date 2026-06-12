---
title: "wireless connection"
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by leg on 2010-01-29
My scenario is that a friends advent laptop would not connect to his wireless connection with the Ubuntu 9.10 I had installed on it for him. I went to have a look and it would not work and ended up bringing it home with me so I take bit more time over solving the problem. Now on my wireless connection I can connect no problem and the only difference I can find is that he has wpa security and I don't. 

Does anyone know if wpa can stop a wireless connection from connecting and if so a way around it.

---

### Post by Idefix82 on 2010-01-29
Some cards and some drivers don't support WPA. What's the card? Please post the relevant line from
```
lspci
```
and the output from
```
lshw -C network
```

---

### Post by leg on 2010-01-29
lspci
```

05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)


```

lshw -C network
```

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:ba:8f:15
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.5 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:27 memory:f7000000-f7000fff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:56:37:04
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:16 ioport:2000(size=256) memory:b0300c00-b0300cff


```

---

### Post by Idefix82 on 2010-01-30
It seems like 9.04 might work better. A did a quick search and lots of people seem to have problems with this card, WPA and 9.10 but many report that 9.04 worked flawlessly.

Before you revert to 9.04 though, try replacing the network manager by wicd, it seems to work better with this card. You can also try this workaround:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/425455/comments/36]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/425455/comments/36")

Let us know how it goes.

---

