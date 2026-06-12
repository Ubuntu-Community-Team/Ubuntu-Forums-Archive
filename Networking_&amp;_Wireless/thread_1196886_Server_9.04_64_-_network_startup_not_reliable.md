---
title: "Server 9.04 64 - network startup not reliable"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by R_Lopez on 2009-06-25
HP DL360 G5 running:
Linux mg05 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:45:36 UTC 2009 x86_64 GNU/Linux
Distributor ID:	Ubuntu
Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty

Concern: Networking does not function after each boot. It sometimes takes a reboot to get it working again. It does not appear to be completely "on" when it is working. The rcconf (apt-get rcconf) does not list networking as a service.

Question: Is there anything in the information below that suggests the root cause of the problem?

root# lspci | grep -i eth
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet (rev 12)
05:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet (rev 12)
0b:00.0 Ethernet controller: Intel Corporation 82571EB Gigabit Ethernet Controller (rev 06)
0b:00.1 Ethernet controller: Intel Corporation 82571EB Gigabit Ethernet Controller (rev 06)
The device in question is the third device above.

root# ip addr show eth0
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:1f:29:5e:5a:62 brd ff:ff:ff:ff:ff:ff
    inet 10.131.0.51/24 brd 10.131.0.255 scope global eth0
    inet6 fe80::21f:29ff:fe5e:5a62/64 scope link 
       valid_lft forever preferred_lft forever

root# netstat -i 
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0     25856      0      0 0         18844      0      0      0 BMRU
lo        16436 0     33084      0      0 0         33084      0      0      0 LRU

root# mii-tool -vv eth0
Using SIOCGMIIPHY=0x8947
SIOCGMIIREG on eth0 failed: Input/output error
<above line repeated in output 22 times>
eth0: negotiated 1000baseT-FD flow-control, link ok
  registers for MII PHY 1: 
    1140 792d 02a8 0380 0de1 c1e1 000f ffffffff
    ffffffff 0200 280f ffffffff ffffffff ffffffff ffffffff 3000
    ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
    ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
  product info: vendor 00:aa:00, model 56 rev 0
  basic mode:   autonegotiation enabled
  basic status: autonegotiation complete, link ok
  capabilities: 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
  link partner: 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD

root# who -r
         run-level 2  2009-06-25 08:13                   last=

(apt-get install chkconfig)
root# chkconfig -l networking:
networking                0:off  1:off  2:off  3:off  4:off  5:off  6:off

root# chkconfig --level 2345 networking on":
insserv: warning: script 'S16linux-restricted-modules-common' missing LSB tags and overrides
insserv: warning: script 'linux-restricted-modules-common' missing LSB tags and overrides
insserv: warning: script 'S16linux-restricted-modules-common' missing LSB tags and overrides
insserv: Service ifupdown has to be enabled to start service networking
insserv: exiting now!
/sbin/insserv failed, exit code 1

after which the status remains the same. The ifupdown is enabled and working.

root # update-rc.d networking defaults
 Adding system startup for /etc/init.d/networking ...
   /etc/rc0.d/K20networking -> ../init.d/networking
   /etc/rc1.d/K20networking -> ../init.d/networking
   /etc/rc6.d/K20networking -> ../init.d/networking
   /etc/rc2.d/S20networking -> ../init.d/networking
   /etc/rc3.d/S20networking -> ../init.d/networking
   /etc/rc4.d/S20networking -> ../init.d/networking
   /etc/rc5.d/S20networking -> ../init.d/networking

after which the status remains the same.

Because the is no "status" for init scripts it is difficult to determine the status of networking (have to look for individual processes). Using tcpdump is the easiest way (see if there is traffic) for me to see if it running.

When the system comes up with networking running dmesg will still have:
root# dmesg | grep eth0
[    2.592943] 0000:0b:00.0: eth0: (PCI Express:2.5GB/s:Width x4) 00:1f:29:5e:5a:62
[    2.592946] 0000:0b:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.593025] 0000:0b:00.0: eth0: MAC: 0, PHY: 4, PBA No: d51930-004
[    5.066066] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.300896] 0000:0b:00.0: eth0: Link is Up 1000 Mbps Full Duplex, Flow Control: None
[    7.302182] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   17.620005] eth0: no IPv6 routers present
[  353.560639] device eth0 entered promiscuous mode
[  373.700121] 0000:0b:00.0: eth0: Link is Down
[  378.780883] 0000:0b:00.0: eth0: Link is Up 1000 Mbps Full Duplex, Flow Control: None
[  385.610008] device eth0 left promiscuous mode

(We are not using IPv6 at this site.)

---

