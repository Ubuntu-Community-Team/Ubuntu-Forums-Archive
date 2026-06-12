---
title: "network card not enabeling"
date: 2006-04-25
forum: Networking &amp; Wireless
---

### Post by Mick-Bungstead on 2006-04-25
hi

My network card is not enabling, the system recognises the card. I restarted the network /etc/init.d/networking restart. i know that the network switch is working because i am using another port on it now with this computer. i have also checked the network cable is plugged in properly. i thought it could be that the network card wasn't plugged in properly and that it wasnt making all connections on the pci slot, but seeing that lshw -C network recognises the card must mean that it is plugged in.

i tried dhclient etho 
$ dhclient eth0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFFLAGS: Device or resource busy
SIOCSIFFLAGS: Device or resource busy
sit0: unknown hardware address type 776
Listening on LPF/eth0/ff:ff:ff:ff:ff:ff
Sending on   LPF/eth0/ff:ff:ff:ff:ff:ff
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
etc etc etc

I did a lshw -C network and got this reply
$ lshw -C network
   *-network DISABLED
        description: Ethernet interface
        product: RTL-8139/8139C/8139C+
        vendor: Realtek Semiconductor Co., Ltd.
        physical id: b
        bus info: pci@00:0b.0
        logical name: eth0
        version: 10
        serial: ff:ff:ff:ff:ff:ff
        size: 100MB/s
        capacity: 100MB/s
        width: 32 bits
        clock: 33MHz
        capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
        configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full link=yes multicast=yes port=MII speed=100MB/s
        resources: ioport:9800-99ff iomemory:ec000000-ec0001ff
 
i then did a ifconfig eth0 and got this reply
$ ifconfig eth0
 eth0      Link encap:Ethernet  HWaddr FF:FF:FF:FF:FF:FF
           BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
           Base address:0x9800

i also tried ifconfig eth0 up 

but i couldnt get it to work.

mick

---

### Post by hw-tph on 2006-04-27
Please post the outputs of the commands **sudo ifconfig** and **dmesg | grep 8139**.


Håkan

---

### Post by Mick-Bungstead on 2006-04-27
$ sudo ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3663 (3.5 KiB)  TX bytes:3663 (3.5 KiB)

$ dmesg | grep 8139
[4294677.642000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294677.642000] 8139cp: pci dev 0000:00:0b.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[4294677.642000] 8139cp: Try the "8139too" driver instead.
[4294677.651000] 8139too Fast Ethernet driver 0.9.27
[4294677.664000] eth0: RealTek RTL8139 at 0x9800, ff:ff:ff:ff:ff:ff, IRQ 0
[4294677.664000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'

---

