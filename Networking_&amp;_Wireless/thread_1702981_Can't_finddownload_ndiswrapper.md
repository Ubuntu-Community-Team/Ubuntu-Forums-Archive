---
title: "Can't find/download ndiswrapper"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by Tydoskus on 2011-03-08
[SIZE=4]I am new to Ubunutu linux and i need a driver for my wireless usb adapter (WNDA3100) but when i try to download ndiswrapper i cant find it with Software Center.[/SIZE]

---

### Post by bkratz on 2011-03-08
The easiest gui way is to use synaptic (system..adminstration..synaptic package manager) and look for ndisgtk. ndisgtk will load all the ndiswrapper files for you and add a menu entry under (system..administration..windows wireless drivers).

---

### Post by Tydoskus on 2011-03-08
Okay so far i found ndiswrapper and i have it installed (it was due to not having a fully updated ubuntu) but i keep getting "invalid driver .inf" messages when i try to install the drivers for my Netgear WNDA3100 can anyone help me?

---

### Post by Yellow Pasque on 2011-03-08
What chipset are we dealing with here? Post output of:
```
sudo update-usbids
sudo lshw -C network
```

---

### Post by Tydoskus on 2011-03-09
[SIZE=3]Im currently connected to a wired connection.[/SIZE]

> --2011-03-09 08:37:53--  [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)
Resolving [www.linux-usb.org]("http://www.linux-usb.org")... 216.34.181.97
Connecting to [www.linux-usb.org|216.34.181.97|:80]("http://www.linux-usb.org%7C216.34.181.97%7C:80")... connected.
HTTP request sent, awaiting response... 200 OK
Length: 447348 (437K) [text/plain]
Saving to: `/var/lib/usbutils/usb.ids.new'

100%[============================================================================>] 447,348      820K/s   in 0.5s    

2011-03-09 08:37:54 (820 KB/s) - `/var/lib/usbutils/usb.ids.new' saved [447348/447348]

Done.

---

### Post by Tydoskus on 2011-03-09
[FONT=Comic Sans MS][SIZE=2]If any of this helps i'm running a M2N68-LA motherboard, AMD Phenom X3 8400 Triple-Core Proccessor, and a Nvidia GeForce 220 Graphics card. 

My usb wireless adapter is (Wireless-N Dual Band WNDA3100) 
I installed what i believe to be the correct driver with Wine and Ndiswrapper.
But Ubuntu doesn't do anything when i plug it in.
[/SIZE][/FONT]

---

### Post by Yellow Pasque on 2011-03-09
Sorry, should have been more clear in last post. Post output of:
```
sudo lshw -C network
```

---

### Post by Tydoskus on 2011-03-09
**[SIZE=2]It says [/SIZE]**
> **PCI (sysfs)**[SIZE=2] 
**for a couple seconds but theres no output?**[/SIZE]

---

### Post by Yellow Pasque on 2011-03-09
Ok, how about:
```
sudo lsusb -vv
```

---

### Post by Tydoskus on 2011-03-09
**[SIZE=2]Also not giving me an output, this time its not even responding[/SIZE]**

---

### Post by Yellow Pasque on 2011-03-09
You have me stumped.

---

### Post by Tydoskus on 2011-03-09
[SIZE=2]Auughh... I'll start a new thread.[/SIZE]

---

### Post by Don1500 on 2011-03-09
> **Tydoskus said:**
> **[SIZE=2]It says [/SIZE]**
[SIZE=2] 
**for a couple seconds but theres no output?**[/SIZE]


Do it again but wait about 10 sec. It's building a response. It should look something like this.
```
sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 20:6a:8a:28:f4:e0
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 duplex=full firmware=sb ip=192.168.2.4 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:45 memory:f0400000-f040ffff
  *-network
       description: Wireless interface
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 18:f4:6a:b4:a5:db
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-27-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0500000-f050ffff

```

---

### Post by Tydoskus on 2011-03-09
[SIZE=2]There must be another problem now. I even rebooted and let Terminal work up the output, but nothing comes up after i put in exactly--
> 
sudo lshw -c network[/SIZE][SIZE=2]or even
[/SIZE]> [SIZE=2]sudo lshw -class network[/SIZE]

[SIZE=2]I just see a glimse of DMI, PCI(sysfs),[/SIZE] [SIZE=2]and[/SIZE] SCSI. 
[SIZE=2]Then it's done.[/SIZE]

---

