---
title: "ASUS X59SL wireless not working - PLEASE HELP"
date: 2009-03-08
forum: Networking &amp; Wireless
---

### Post by arsla on 2009-03-08
Hi gals and guys :D

I have a Ubuntu 8.10 on my ASUS X59SL and I can not get the wireless going.
There simply is no 'wireless network' in the Network Manager. However there is an active wireless driver in Hardware Drivers.
I was wondering if anyone has any suggestions.

Thanks :D

PS
Here are the outputs of some commands that I have seen people post with such problems :D
lspci

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


lsusb

Bus 003 Device 005: ID 0bda:0116 Realtek Semiconductor Corp. Mass Storage Device
Bus 003 Device 003: ID 174f:5a35 Syntek 1.3MPixel Web Cam - Asus G1s
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 002 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


lshw -class network

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:22:15:b2:c1:41
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis190 driverversion=1.2 ip=192.168.1.64 latency=0 module=sis190 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: d6:58:1d:7c:6c:17
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


ifconfig

eth0      Link encap:Ethernet  HWaddr 00:22:15:b2:c1:41  
          inet6 addr: fe80::222:15ff:feb2:c141/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14795 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14451 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15648556 (15.6 MB)  TX bytes:2237414 (2.2 MB)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)


iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by shanix on 2009-03-08
Looks like this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/275423](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/275423)

---

### Post by arsla on 2009-03-08
> **shanix said:**
> Looks like this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/275423](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/275423)

Can not really find the similarity. :(

I should add that the LED for wireless does briefly turn on during boot but turns off after 2-3 seconds while the bluetooth remains turned on. Bluetooth works just fine.

oh yeah and I am kind of a beginner when it comes to Linux :)


PS

SORRY! I did not see the link to the 'how-to'! :D
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)
I'll try it now :D

---

### Post by arsla on 2009-03-08
Worked great! Thank youuuuuu!!!! :d

---

