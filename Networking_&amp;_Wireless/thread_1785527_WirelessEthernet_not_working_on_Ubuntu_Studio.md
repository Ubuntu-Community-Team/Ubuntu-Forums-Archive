---
title: "Wireless/Ethernet not working on Ubuntu Studio"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by Black Angel Aster on 2011-06-18
Hi, so basically, I installed Ubuntu Studio 11.04 on my Dell Inspiron 530s Desktop 3 days ago. Before this, I had Ubuntu (normal.. I guess). Everything is working absolutely great! I'm not new on Ubuntu, so I know how to use the interface and everything.. but I have this Recurring problem with every dist. of Ubuntu...

My Ethernet only works 1 in about 30 boots. Every time I boot up, I HAVE to restart network-manager with 


```
sudo service network-manager stop

sudo service network-manager start
```


But that only gets my Wi-Fi working.. And plus, it disconnects all the time... (which, isn't great, considering that my computer is very far from my router and I really need Ethernet for a relatively good internet access.)

So as I said, my Ethernet is having huge problems, which is very inconvenient. But, it works fine with Windows Vista (dual Booting with Windows Vista). So I don't think anything is broken, really. 

Oh, and my system is on 64-bit..

---

### Post by nbound on 2011-06-18
whats the output of **sudo lshw -C network**

---

### Post by Black Angel Aster on 2011-06-18
The output of **sudo lshw -C network** is:

 ```
 *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:01:a5:88
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 firmware=1.1-2 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:41 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:ff00(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:22:75:0c:7a:e8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.38-8-generic firmware=0.12 ip=192.168.2.7 link=yes multicast=yes wireless=IEEE 802.11bgn
```

I don't understand any of it... So I can't determine what it means...

[EDIT]

So, I guess, it detects my Etho Adapter, but doesn't know how to use it?

---

### Post by TheDoctorX on 2011-06-18
uuuuh ... i had the same problem a week ago ... people told me it was a defect of the network manager, but nobody could help me ... then i tryed to update and suddently it started to work!! so try to update completly from the update manager ... if doesn't work i don't know what to do ...
hope it could be useful:)

---

### Post by Black Angel Aster on 2011-06-18
> **TheDoctorX said:**
> people told me it was a defect of the network manager, but nobody could help me ... then i tryed to update and suddently it started to work!! so try to update completly from the update manager ... 

Yeah, there's no updates for the network manager, I already tried it. Thanks though...

---

### Post by Black Angel Aster on 2011-06-19
Anyone? Know how to fix this?

---

