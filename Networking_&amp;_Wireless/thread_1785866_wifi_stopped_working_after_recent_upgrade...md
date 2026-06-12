---
title: "wifi stopped working after recent upgrade.."
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by zander1013 on 2011-06-18
hi,

i have a dell 1501 that has been upgraded from 10.10 to 11.04. everything was working okay. and then the user ran an upgrade recently. subsequently the wifi has mysteriously stopped working. it connects okay if one plugs it directly into the router but the wifi seems to have just stopped working.

my mini 9 connects fine to the netgear wifi router using wireless.

when i run the system tests for networking i get the errors...
"root could not find def gateway info /proc"
"root could not find default gateway by running route"

here is the output from some diagnostic commands.

NOTE:this is similar to a post titled "wi-fi dead?" but the output is not quite the same...

lauren@lauren-Inspiron-1501:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

lauren@lauren-Inspiron-1501:~$  iwconfig wlan0
wlan0     No such device


lauren@lauren-Inspiron-1501:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:57:14:eb
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.10.74 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:21 memory:c0300000-c0301fff
lauren@lauren-Inspiron-1501:~$ 




lauren@lauren-Inspiron-1501:~$  iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lauren@lauren-Inspiron-1501:~$ 



lauren@lauren-Inspiron-1501:~$ lsb_release -d
Description:	Ubuntu 11.04
lauren@lauren-Inspiron-1501:~$ 



lauren@lauren-Inspiron-1501:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
lauren@lauren-Inspiron-1501:~$ 


OBSERVE: the output is not quite the same as the other thread.

please advise.

thank you.:popcorn:

---

### Post by zander1013 on 2011-06-18
hi,

i marked this thread as SOLVED because the issue is discussed in the sticky thread here [http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)


but i have not got my wifi to work yet..

---

### Post by zander1013 on 2011-06-20
hi,

i found a solution that worked for me here...
[http://computerandu.wordpress.com/20...-ubuntu-11-04/](http://computerandu.wordpress.com/20...-ubuntu-11-04/)

i removed the sta driver and then deployed Alternate Solution 2 given in the link. i do hope it works for you.:popcorn::KS

---

### Post by zander1013 on 2011-06-20
here is the correct link.

[http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/)

---

