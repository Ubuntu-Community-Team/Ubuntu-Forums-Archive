---
title: "I see the nextwork, Broadcom 4312 does not connect."
date: 2011-11-25
forum: Networking &amp; Wireless
---

### Post by Jboulden on 2011-11-25
Hello, Having terrible trouble connecting to a wireless network after the re-installation of Ubuntu 10.04.  I installed 11.04 but ran into a bios issue that prevented the USB connections from functioning properly.  That's another thread.  

At any rate, I can see the network, but cannot connect using the B43 driver.  The STA driver does not even show the network.  I have followed the steps in the comprehensive guide and nothing.  Here's the critical information:

1.  Make and Model: Dell Inspiron 1546

2.  (lspci): Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01) 
(lsusb) Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Hama Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:63ee Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

3.  wlan0     Link encap:Ethernet  HWaddr 70:1a:04:c6:e8:73  
          inet6 addr: fe80::721a:4ff:fec6:e873/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:408 (408.0 B)

4. lsmod  - attached

5. dmesg - attached as well

6.  Network 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: a4:ba:db:97:60:1e
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.103 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:28 ioport:de00(size=256) memory:f0010000-f0010fff(prefetchable) memory:f0000000-f000ffff(prefetchable) memory:f0020000-f003ffff(prefetchable)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:f7bfc000-f7bfffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 70:1a:04:c6:e8:73
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

7. Scanning for networks: wlan0     No scan results

8.  Description:    Ubuntu 10.04.3 LTS

9. Kernel architecture: 2.6.32-35-generic-pae i686

10.  jeffb@jeffb-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                        Ignoring unknown interface eth0=eth0.
                                                                                                       [ OK ]

---

