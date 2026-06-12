---
title: "No Wireless"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by phoynak on 2009-02-25
I just used Kernelcheck to update to the latest kernel since the last update from the Ubuntu's autoupdate killed all of my network access. I was tired of manually booting into an older kernel. Well now the wired connection is working but I have no wireless. I assume its a driver issue. I have a Dell Mini 9.... how do I check if the wireless is active and fix the driver? I use Wicd for my network management.


thanks

---

### Post by superprash2003 on 2009-02-25
in your terminal type the following commands and post its output
1)ifconfig
2)iwconfig
3)lshw -C network

---

### Post by phoynak on 2009-02-25
Ok here you go...

eth0      Link encap:Ethernet  HWaddr 00:21:70:d8:13:67  
          inet addr:10.11.215.111  Bcast:10.11.215.255  Mask:255.255.252.0
          inet6 addr: fe80::221:70ff:fed8:1367/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37749 (37.7 KB)  TX bytes:13740 (13.7 KB)
          Interrupt:252 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

 *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:d8:13:67
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=10.11.215.111 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 66:3b:5d:21:ed:90
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by superprash2003 on 2009-02-26
you seem to have a broadcom chipset.. try this [http://www.prash-babu.com/2008/11/how-to-configure-broadcom-wireless-in.html](http://www.prash-babu.com/2008/11/how-to-configure-broadcom-wireless-in.html) .. if this doesnt work try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

