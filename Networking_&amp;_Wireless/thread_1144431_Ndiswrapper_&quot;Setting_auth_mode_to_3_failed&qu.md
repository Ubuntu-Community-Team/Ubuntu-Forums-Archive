---
title: "Ndiswrapper: &quot;Setting auth mode to 3 failed&quot;"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by Guitarmaster316 on 2009-04-30
Hello,

I was able to get my wireless card to work through ndiswrapper :)  however, I can't access encrypted networks.  I suspect the following is he reason.

```
matt@matt-laptop:~$ dmesg | grep -e ndis -e wlan0
[   20.382499] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   20.480358] usbcore: registered new interface driver ndiswrapper
[   26.173940] usbcore: deregistering interface driver ndiswrapper
[   26.191695] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   26.270026] ndiswrapper: driver bcmwl5 (Linksys,02/12/2003, 3.10.39.7) loaded
[   26.270497] ndiswrapper 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[   26.361282] ndiswrapper: using IRQ 10
[   26.573305] wlan0: ethernet device 00:90:4b:42:d4:a8 using NDIS driver: bcmwl5, version: 0x50000, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[COLOR="Red"][   26.573453] ndiswrapper (set_ndis_auth_mode:619): setting auth mode to 3 failed (C0010015)
[   26.573458] wlan0: encryption modes supported: none[/COLOR]
[   26.575998] usbcore: registered new interface driver ndiswrapper
[   33.894278] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   69.190957] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   79.332045] wlan0: no IPv6 routers present
matt@matt-laptop:~$ 

```

I don't know what auth mode 3 is and why it failed.

I am running Jaunty on an hp ze4560 with a Broadcom 4306 (rev2) card.

Ittiam tried their best to help me out, but to no avail (special thanks).

When I blacklist b43legacy, the network stops working and wlan0 disappears.  It then says that ndiswrapper couldn't initialize the device.

```
matt@matt-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wlan0
       version: 02
       serial: 00:90:4b:42:d4:a8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Linksys,02/12/2003, 3.10.39 ip=172.16.1.112 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0d:9d:5a:97:ba
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: a2:95:e3:55:1f:63
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
matt@matt-laptop:~$
```

```
matt@matt-laptop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
matt@matt-laptop:~$
```

This is all the information I can think of to post right now.

Any ideas???

Thanks!

---

### Post by Guitarmaster316 on 2009-05-30
Bump

---

