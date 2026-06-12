---
title: "No Wireless Connection after testing with Windows"
date: 2011-12-01
forum: Networking &amp; Wireless
---

### Post by LearningPerson on 2011-12-01
Hello,  I was almost there when I tested my TL-WN722N USB Adapter on the Windows partition as I was having trouble with it working with Lucid 10.04.  After that (or something), I could no longer see my neighbor's wifi addresses.

Troubleshooting said to make sure the Atheros card was turned on and my output from sudo lshw -C network was that the wireless device was Unclaimed.  I enabled Atheros in Windows but still No Wireless Connection when I cam back to Lucid.

Used to see wlan0; the ESSID and even a couple of times: the access point of the neighbor who will share bandwidth with me.

I removed Network Manager and installed WICD.

Sure hope someone can help. 

Thanks.


Truly I

---

### Post by bluexrider on 2011-12-01
what was the print of lshw -C network

---

### Post by LearningPerson on 2011-12-01
Hi bluexrider,

Here it is:
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:feaf0000-feafffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 00:26:18:30:30:02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.3 latency=0 multicast=yes
       resources: irq:26 ioport:e800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdff8000-fdffbfff(prefetchable) memory:febe0000-febfffff(prefetchable)


Thanks, Sharon

---

### Post by bluexrider on 2011-12-01
The wireless card has no driver configured for it.

try this link [http://ubuntuforums.org/showthread.php?t=1484924](http://ubuntuforums.org/showthread.php?t=1484924)

hope this helps

---

### Post by LearningPerson on 2011-12-02
Hi,

I booted into linux kernel 2.6.32-34 rather than the 2.6.32-35 I had been in.  The wireless connections all showed.

Here is the output of  lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:23:00:33:05
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.32-34-generic-pae firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:feaf0000-feafffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 00:26:18:30:30:02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.3 latency=0 multicast=yes
       resources: irq:26 ioport:e800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdff8000-fdffbfff(prefetchable) memory:febe0000-febfffff(prefetchable)
 
Still can't connect though so what should I do now?

Thanks, Sharon

---

### Post by bluexrider on 2011-12-03
looking at the configuration you should be able to connect using the network manager

---

### Post by fdrake on 2011-12-03
post the output of 
```

rfkill list all

```

---

### Post by LearningPerson on 2011-12-03
Hi bluexrider,

Well, I disconnected my TL-WN722N and it actually works  --- slightly, weakly and for not more than 5 minutes.  I believe I am picking up directly from my neighbor with his password.  

I have ordered an Alfa AWUS036H 1000mW 1W 802.11b/g USB Wireless WiFi network Adapter with 5dBi Antenna for Linux.  Hopefully that will work better.  

I won't say this situation is solved with the TL-WN722N and my system but hopefully will be able to with the Alfa.

Thanks, Sharon

---

### Post by LearningPerson on 2011-12-03
Here it is:

 rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

