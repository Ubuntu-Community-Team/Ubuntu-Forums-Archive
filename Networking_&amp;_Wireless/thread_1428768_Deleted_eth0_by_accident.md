---
title: "Deleted eth0 by accident"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by thairsadi77 on 2010-03-13
i had deleted eth0 by accident how can i restore it

---

### Post by gradinaruvasile on 2010-03-13
> **thairsadi77 said:**
> i had deleted eth0 by accident how can i restore it

And how exactly did you managed to do that?

---

### Post by thairsadi77 on 2010-03-13
> **gradinaruvasile said:**
> And how exactly did you managed to do that?
i tried to add an isp connection so i go to eth0 and press edit but i think i pressed delete instead lol

---

### Post by warfacegod on 2010-03-13
> **gradinaruvasile said:**
> And how exactly did you managed to do that?

I guess the easiest way would be to highlight it in Network Connections and click delete.:p

thairsadi77: Try going into System> Prefs.> Network Connections and click add. Under the Wired tab name it Auto eth0, check connect automatically, MTU should be automatic, and if there is more than one user on your computer check Available to all users.

---

### Post by gradinaruvasile on 2010-03-13
Lol that is a dhcp connection profile, not eth0...

---

### Post by thairsadi77 on 2010-03-14
> **gradinaruvasile said:**
> Lol that is a dhcp connection profile, not eth0...
 would you explain more please ...i am new to linux

---

### Post by Iowan on 2010-03-14
I'm kinda curious myself...
Perhaps it's the difference between the Auto Eth0 connection and the hardware referenced as "eth0".

---

### Post by V.V.V. on 2010-10-19
Hi guys, I've got the same problem — clicked "Delete" in the Network Conections window. Now my NIC isn't listed by lspci and it's LED is off despite the connected cable. Any ideas how to bring the ethernet connection back?

---

### Post by Iowan on 2010-10-19
Although I haven't tried it, you *should* be able to add it back in Network Manager.

---

### Post by V.V.V. on 2010-10-20
> **Iowan said:**
> Although I haven't tried it, you *should* be able to add it back in Network Manager.
I can add any count of the network connections in the manager, but they don't bind to my NIC. I.e. the network card LED still isn't lit, the card isn't listed by lspci, and also, when I activate the new created connection it turns off my other wired connection (I have two NICs).

---

### Post by Iowan on 2010-10-20
Does it (the interface) show up in **sudo lshw -C network**?

---

### Post by V.V.V. on 2010-10-20
> **Iowan said:**
> Does it (the interface) show up in **sudo lshw -C network**?

The output:
```
vvv@vvv-desktop:~$ sudo lshw -C network
[sudo] password for vvv: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:4d:91:3a:3c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=172.30.5.5 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:30 ioport:d000(size=256) memory:f9000000-f9000fff memory:fac00000-fac1ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

The first interface the command outputs is my working card. The deleted card's MAC got to be 00:0a:cd:15:52:7a, and it's name was eth0 before deletion. What is the second "disabled" entry — I don't know.

---

