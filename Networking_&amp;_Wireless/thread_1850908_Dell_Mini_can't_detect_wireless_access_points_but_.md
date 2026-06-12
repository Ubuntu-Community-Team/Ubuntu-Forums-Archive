---
title: "Dell Mini can't detect wireless access points but can connect to modem/routers"
date: 2011-09-27
forum: Networking &amp; Wireless
---

### Post by scared_ghost on 2011-09-27
Hello, 
I have a dell mini which I have just installed a fresh copy of Ubuntu on (11.04). I have updated it as well. The problem is that when I try to use it on a work network wirelessly it can't even detect the wireless access points. It works fine if you connect to the router/modem (tried it on different ones), still wirelessly and  fine with an ethernet cable. So any ideas? I have pasted some of the info that seems to get requested in these posts below if that means anything to any one. 

thanks in advance

ghost@drone:~$ rfkill list all
1: compal-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: compal-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
5: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no



 sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:23:08:18:a0:da
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:c8:a6:ff
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f0610000-f0610fff memory:f0600000-f060ffff memory:f0620000-f063ffff

---

### Post by chili555 on 2011-09-27
I don't believe wl is the correct driver for your device. Please hook up the ethernet cable, get a connection and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-lpphy-installer
```After it's done, reboot and let us have your report.

---

### Post by scared_ghost on 2011-09-27
YES!!!  Thank you so much. Works like a dream. 

Also How did you diagnose the problem?

---

### Post by chili555 on 2011-09-27
> **scared_ghost said:**
> YES!!!  Thank you so much. Works like a dream. 

Also How did you diagnose the problem?My clue was here:> BCM4312 802.11b/g [COLOR="Red"]LP-PHY[/COLOR]A little googling and a few years of experience suggested that this is the answer:> firmware-b43-[COLOR="Red"]lpphy[/COLOR]-installerI'm glad it's working now.

Would you please use the thread tools at the top and Mark Solved?

---

### Post by scared_ghost on 2011-09-27
done thanks again

---

