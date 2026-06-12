---
title: "WIFI not work after sleep/suspend"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by maximilianyuen on 2009-12-08
my notebook is Asus Pro 8
and I am using wicd, network manager keep disconnecting.

my wifi works perfectly when first boot
however is it goes sleep/suspend, the wifi will dead
can;t detect any network at all

```

*-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:25:d3:bf:78:f4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.1.11 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:feaf0000-feafffff

```

wonder is there any way for me to turn off and on the network card?
or are there any solutions?

many thanks

---

### Post by maximilianyuen on 2009-12-08
or at least tell me what is the keyword for me to google.....:(

---

### Post by maximilianyuen on 2009-12-10
no one :(

---

### Post by deadvirus on 2011-08-17
I also have this problem on my Asus K52Jc (also uses an atheros card). I usually reaload the ath9k driver module and it works again:

```
sudo modprobe -r ath9k
sudo modprobe ath9k
```

---

### Post by teddybar on 2011-10-31
> **deadvirus said:**
> I also have this problem on my Asus K52Jc (also uses an atheros card). I usually reaload the ath9k driver module and it works again:

```
sudo modprobe -r ath9k
sudo modprobe ath9k
```

Many thx, this work for me.

---

