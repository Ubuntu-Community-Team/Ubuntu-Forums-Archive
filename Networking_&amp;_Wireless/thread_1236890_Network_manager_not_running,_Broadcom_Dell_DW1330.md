---
title: "Network manager not running, Broadcom Dell DW1330"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by ironslave on 2009-08-10
My networkmanager refuses to run, i was attemping to install flash on firefox with no luck at all, on installation it had a popup about moving a file somwhere for some reason and when i rebooted my network manager would not load, i have rebooted several times allready

the driver is still installed and it is being picked up when i run the command from the ubuntu help

i tried running

sudo /etc/init.d/NetworkManager start (and restart, stop, force-reload), but i get nothing
the enable networking is checked and cannot be undone, any suggestion?


running jaunty on and acer aspire one D150

i opened up nm-system-settings.conf
Previously, it was the following:
[ifupdown]
managed=false

I changed to the following:
[ifupdown]
managed=true
it still will not load

---

### Post by ironslave on 2009-08-10
```

sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 00:1e:4c:3b:58:7c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  **_*-network DISABLED_**
       description: Ethernet interface
       product: L1e Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:23:5a:54:86:36
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no module=atl1e multicast=yes port=twisted pair
  **_*-network DISABLED_**
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 36:92:4e:9b:e8:7f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
james@ubuntu:~$ 


```

---

### Post by ironslave on 2009-08-11
Problem solved

I ran
sudo nautilus
Navigated to /usr/sbin
right clicked networkmanager
allowed to be ran as executable

sudo /etc/init.d/NetworkManager restart

all is well :P

I found the solution by putting echos on /etc/init.d/NetworkManager until i found its exit point.

apparently the 'test -x' was saying the package failed testing, so I removed it and it executed.
while restarting the network manager i got a permission denied from the script.
I changed the above metioned and put the test -x back in and it runs fine now :P

---

