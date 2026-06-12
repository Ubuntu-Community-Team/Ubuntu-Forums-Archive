---
title: "Wireless not working on Dell XPS m1530 with Broadcom BCM4328 802.11a/b/g/n"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by mknapik on 2010-06-29
I've recently lost the ability to connect to wifi networks.  The wifi network icon does not show up in the top right of the screen, near the date/time.

I've gone through the Wifi troubleshooting guide here: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lsmod](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lsmod)

Everything seems to be ok.  I have a native driver, and I can run sudo iwlist scan and see available networks.

However, I cannot connect to any of the networks. Can anyone provide some help?

Here is some additional info based off of this page: [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

lspci gives me:
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)

iwconfig gives me:
eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:170
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

lsmod gives me
wl                   1964968  0 

dmesg | grep 'eth' gives me:
[    0.920304] sky2 eth0: addr 00:23:ae:0f:b5:17
[    9.450210] eth1: Broadcom BCM4328 802.11 Hybrid Wireless Controller 5.60.48.36 
[   23.224335] sky2 eth0: enabling interface
[   23.225174] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.752520] eth1: no IPv6 routers present
[  310.311008] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[  310.311823] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  320.380910] eth0: no IPv6 routers present

sudo lshw -C network gives me:
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:23:ae:0f:b5:17
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.2.176 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:f1ffc000-f1ffffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 03
       serial: 00:24:2b:bb:7c:58
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f1efc000-f1efffff memory:f0000000-f00fffff(prefetchable)

iwlist scan gives me:
eth1      Interface doesn't support scanning.

NOTE - This looks different than it gave me before. I didn't do anything except for reboot the computer since last checking it though.

lsb_release -d gives me:
Description:	Ubuntu 10.04 LTS

uname -mr gives me:
2.6.32-22-generic x86_64

sudo /etc/init.d/networking restart gives me:
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

---

