---
title: "Can't connect to internet (Intel 2200BG/HP NC62200"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by yorkshiresky on 2009-03-11
I'm totally stumped in trying to get my wireless connection to work. I installed 8.10 on Saturday and it connected straight away but soon after it lost the connection and have looked at dozens of threads in the hope of finding what's up with no joy. I did a fresh install of 8.10 today but that didn't work either.

Here are the results of some scans

home@home-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 11
       serial: 00:12:79:c6:7a:97
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5751m-v3.29a latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3a:12:ff:02:54:3e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
home@home-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

home@home-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                    [OK]
home@home-laptop:~$ iwconfig
lo        no wireless extensions

eth0      no wireless extensions

pan0      no wireless extensions



Network manager doesn't work either.

I'm a linux newbie and know it's a bit of a learning curve but this has me floored.

---

