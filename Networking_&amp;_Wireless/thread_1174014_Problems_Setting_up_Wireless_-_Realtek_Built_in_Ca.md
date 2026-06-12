---
title: "Problems Setting up Wireless - Realtek Built in Card"
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by FacelessDavisk on 2009-05-30
I have a Gateway M6750(originally ran Windows Vista - 32bit), trying to get Ubuntu to get wireless. I'm only running Ubuntu 9.04 on this laptop now(but have Windows desktop with working wireless)
My wireless card is a Marvell MC85 (or Realtek rather I believe, RTl8101E/RTL8102E PCI Express).

I've downloaded the driver(I believe the correct one, the Realtek Network Driver)

Then unzipped the .exe file, went into the /WINVISTA/32/ directory, and used ndiswrapper on the netrtx.INF file inside it.

I get an error saying "Unable to see if hardware is present."
Then in the GUI of ndiswrapper, the netrtx32 is listed and saying "Hardware present: Yes"

I've ran ndiswrapper in both gui and command line for this.

ifconfig wlan0 up  gives me "wlan0:ERROR while getting interface flags: No such device"

I've read who knows how much, from when I understand what people are talking about, their results are inconclusive, and the rest...I didn't understand. Any help is appreciated. This will be my first time trying to set up wireless on Ubuntu, and from what I gather, this wireless card sucks for Ubuntu(but possible).

$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:b8:e2:f6:8b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.70 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: a6:b4:0d:ff:3a:b6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by superprash2003 on 2009-05-30
post output of lshw -C network from the terminal

---

### Post by FacelessDavisk on 2009-05-30
bumped

---

