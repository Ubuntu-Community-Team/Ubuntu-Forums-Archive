---
title: "Driver for Thomson Wireless 802.11G USB Adapter"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by wesmcdermott on 2010-09-01
Hi,

I'm a complete newb to Ubuntu but I thought I'd install it for the sake of keeping sane (ex Windows user, fingers crossed). I'm trying to get my very old PC to run wireless. Previous windows installations ran the adapter with no problems at all, but ubuntu can't seem to find the driver. Where do I get one from or what needs to be done to get this thing to work?

Wes

---

### Post by lukeiamyourfather on 2010-09-01
How did you determine that the wireless adapter was not recognized? When you click on the network icon in the top right are there any adapters listed?

---

### Post by wesmcdermott on 2010-09-01
I've inserted the USB and it didnt show any signs of recognising it. Whereas when I inserted the adapter into the pc when windows was installed the light on the adapter came on. In Ubuntu nothing happened.

I've checked the networks available and there's nothing showing.

Wes

---

### Post by lukeiamyourfather on 2010-09-01
Boot the system with the adapter already plugged in, then run this command in the terminal and post the output here.

```
sudo lshw -class network
```

---

### Post by wesmcdermott on 2010-09-01
This is what I get:

```
*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:03:02.0
       logical name: eth0
       version: 10
       serial: 00:11:d8:c3:52:bf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:21 ioport:e400(size=256) memory:cffff400-cffff4ff
```

---

### Post by lukeiamyourfather on 2010-09-02
> **wesmcdermott said:**
> This is what I get:

```
*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:03:02.0
       logical name: eth0
       version: 10
       serial: 00:11:d8:c3:52:bf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:21 ioport:e400(size=256) memory:cffff400-cffff4ff
```

Looks like the wireless adapter was indeed not recognized. I tried to find more information about that company but it appears as though it no longer exists. Since it was not very popular to begin with and is now defunct, I doubt you'll find proper drivers for it on Linux. A newer adapter that is supported in Linux can be had for $10-15.

---

