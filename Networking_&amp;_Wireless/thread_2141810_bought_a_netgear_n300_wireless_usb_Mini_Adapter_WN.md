---
title: "bought a netgear n300 wireless usb Mini Adapter WNA3100M, but cannot make it work"
date: 2013-05-03
forum: Networking &amp; Wireless
---

### Post by Bondt on 2013-05-03
Hi,

I just bought a smallest wireless usb adapter: netgear n300 wireless usb Mini Adapter WNA3100M, and cannot make it work. 
Surfed a lot for possible solutions, but all failed.  Any ideas? 

with many thanks
Bondt.

   Bondt@ubuntu:~$ ndiswrapper -l 
 netwna3100m : driver installed 
     device (0846:9021) present (alternate driver: rtl8192cu) 
 

 Bondt@ubuntu:~$ lsusb 
 Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
 Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
 Bus 001 Device 003: ID 03f0:034a Hewlett-Packard  
 Bus 001 Device 007: ID 03f0:094a Hewlett-Packard  
 Bus 001 Device 005: ID 0bda:0184 Realtek Semiconductor Corp.  
 Bus 002 Device 003: ID 0846:9021 NetGear, Inc.  
 

 Bondt@ubuntu:~$ uname -m 
 i686 
 

 Bondt@ubuntu:~$ sudo lshw -C Network 
   *-network                
        description: Ethernet interface 
        product: 82579LM Gigabit Network Connection 
        vendor: Intel Corporation 
        physical id: 19 
        bus info: pci@0000:00:19.0 
        logical name: eth0 
        version: 04 
        serial: 6c:3b:e5:3e:81:58 
        size: 100Mbit/s 
        capacity: 1Gbit/s 
        width: 32 bits 
        clock: 33MHz 
        capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k duplex=full firmware=0.13-4 ip=192.168.2.110 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s 
        resources: irq:41 memory:f7c00000-f7c1ffff memory:f7c39000-f7c39fff ioport:f080(size=32) 
   *-network 
        description: Wireless interface 
        physical id: 2 
        logical name: wlan0 
        serial: 00:8e:f2:8c:d0:f5 
        capabilities: ethernet physical wireless 
        configuration: broadcast=yes driver=ndiswrapper+netwna3100m driverversion=1.58rc1+NETGEAR, Inc.,11/28/2011 link=no multicast=yes wireless=IEEE 802.11g 
 


 Bondt@ubuntu:~$ lsmod | grep ndis 
 ndiswrapper           196777  0  
 

 Bondt@ubuntu:~$ dmesg | grep -e ndis -e wlan 
 [    6.139602] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no) 
 [    7.182646] ndiswrapper: driver netwna3100m (NETGEAR, Inc.,11/28/2011,1015.4.1128.2011) loaded 
 [    8.666594] wlan0: ethernet device 00:8e:f2:8c:d0:f5 using NDIS driver: netwna3100m, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8192C Wireless LAN USB NIC                                     ', 0846:9021.F.conf 
 [    8.666612] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK 
 [    8.666649] usbcore: registered new interface driver ndiswrapper 
 [   10.536453] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 [ 1600.181161] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 [ 1607.044944] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 [ 1711.960886] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 [ 1718.860809] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 [ 1929.793771] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 [ 1930.329856] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 [ 1938.031693] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
 [ 2153.758403] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 [ 2153.766347] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 [ 2154.267627] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 [ 2161.880752] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
 [ 2215.653510] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 [ 2215.661567] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 [ 2293.371470] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 [ 2293.910234] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by Alita99 on 2013-07-17
I have the same problem, thanks to help!

---

