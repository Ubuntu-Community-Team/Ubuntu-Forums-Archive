---
title: "Help! no wifi connection after my first installation of ubuntu:-("
date: 2012-03-13
forum: Networking &amp; Wireless
---

### Post by ruslanbe on 2012-03-13
i have sl400 lenovo laptop. 
wifi card - intel wimax link5150 agn. 
 after installation i can't find my home wifi (in windows 7 it worked great)
i am new using linux/ubuntu so please help me as detail as you can. 
sudo lshw -C network
*-network UNCLAIMED     
       description: Network controller
       product: WiMAX/WiFi Link 5150
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:fd6fe000-fd6fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:8c:96:b8:d2
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=10.0.0.6 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:46 ioport:e800(size=256) memory:f8fff000-f8ffffff memory:f8fe0000-f8feffff memory:f8f00000-f8f0ffff
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       bus info: usb@1:2
       logical name: wmx0
       serial: 00:1d:e1:01:9f:61
       capabilities: ethernet physical
       configuration: driver=i2400m firmware=i2400m-fw-usb-1.5.sbcf link=no
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: wwan0
       serial: 02:80:37:ec:02:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=Mobile Broadband Network Device link=no multicast=yes
lspci -nnk | grep -iA2 net
ruslan@ruslan-ThinkPad-SL:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Intel Corporation WiMAX/WiFi Link 5150 [8086:423d]
    Subsystem: Intel Corporation WiMAX/WiFi Link 5150 AGN [8086:1211]
    Kernel modules: iwlagn
0c:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: Lenovo Device [17aa:2108]
    Kernel driver in use: r8169
iwconfigruslan@ruslan-ThinkPad-SL:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmx0      no wireless extensions.

wwan0     no wireless extensions.
rfkill list all
ruslan@ruslan-ThinkPad-SL:~$ rfkill list all
1: i2400m-usb:1-2:1.0: WiMAX
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

THANKS!!

---

### Post by gordintoronto on 2012-03-14
This may have the solution:

[https://lists.ubuntu.com/archives/kernel-bugs/2010-October/145827.html](https://lists.ubuntu.com/archives/kernel-bugs/2010-October/145827.html)

---

### Post by ruslanbe on 2012-03-14
nope..still not working..
i habe the wire internet working but the wofi is not..
any ideas?

---

