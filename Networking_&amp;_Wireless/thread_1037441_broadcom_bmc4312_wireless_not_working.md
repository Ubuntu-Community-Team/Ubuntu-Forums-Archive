---
title: "broadcom bmc4312 wireless not working"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by drinkmocha on 2009-01-11
Please help.

I did a clean install of 8.10. On the liveUSB I was able to connect to wireless (WPA2) without problems. But after installing Ubuntu, I don't see any wireless networks at all. I already activated the Broadcom Driver under Hardware Settings but still don't see anything after a few restarts and install/uninstall of the driver.

I'm using a netbook; Lenovo S10.

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:26:ec:11
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 ip=192.168.0.196 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:23:4d:de:1d:76
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: be:c8:7b:e2:7c:98
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


--------------

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   



Please help. Thank you.

---

### Post by Ayuthia on 2009-01-11
The only way that I have seen the Broadcom STA module work on a Lenovo S10 is by compiling the wl driver manually:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

There are instructions in the README.txt file at that link that should help.

---

### Post by drinkmocha on 2009-01-11
thanks, i'll try that

---

### Post by drinkmocha on 2009-01-11
okay i tried to follow that, but on the last part i'm getting this message:

insmod: error inserting '/home/ggg/hybrid_wl/wl.ko': -1 file exists

anybody know what this means?

---

