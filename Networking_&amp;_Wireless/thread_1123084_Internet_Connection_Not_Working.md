---
title: "Internet Connection Not Working"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by diedo on 2009-04-11
Hello All I'm facing a really big anyoing trouble and weird :cry:

when i start the live DVD the the NetowrkManager shows that my connection disconnected in the main time the router working and the Ethernet connector plugged correctly

more details :

1- First My Machine is Dell Inspiron 1300 With Broadcom Ethernet Card
2- the Driver For my Broadcom Ethernet Completely installed and all of it's kernel modules are loaded
3- when i plugged my cable through another router the connection was detected and worked perfectly
4 - my router is called EncoreDSL with 4 ports
5 - The router that worked with me was speed touch

THE WHOLE THING IS I CAN"T CONNECT TO MY WEIRD DSL CONNECTION THROUGH MY ROUTER :cry:

POSTED : i have another Linux distro installed FEDORA 10

Thanks

---

### Post by Crafty Kisses on 2009-04-11
What are the results of these commands?
```
lshw -C network
lspci
ifconfig
iwconfig
```

---

### Post by Ryuhayabusa on 2009-04-11
> **Codename said:**
> What are the results of these commands?
```
lshw -C network
lspci
ifconfig
iwconfig
```

[COLOR="Teal"]open a terminal and type them in one at a time and press enter[/COLOR]

---

### Post by diedo on 2009-04-11
> **Codename said:**
> What are the results of these commands?
```
lshw -C network
lspci
ifconfig
iwconfig
```



Here it is 

> diedo-laptop ~ # lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:65:ad:61
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:94:7c:25
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6e:56:c0:23:f9:36
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

========================================================================================================================================================

diedo-laptop ~ # lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

==========================================================================================================================================================
eth0      Link encap:Ethernet  HWaddr 00:15:c5:65:ad:61  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:229 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16217 (16.2 KB)  TX bytes:30529 (30.5 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:902 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65640 (65.6 KB)  TX bytes:65640 (65.6 KB)
===========================================================================================================================================================
diedo-laptop ~ # iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


---

### Post by diedo on 2009-04-12
May some one answer me PLease :cry: 

BUMP :cry:

---

### Post by diedo on 2009-04-12
????

---

### Post by diedo on 2009-04-12
NO ONE HELPS :cry:

---

### Post by doas777 on 2009-04-12
ok, your command indicates that you do not have an IP address for eth0.
try this command:
```
sudo ifup eth0
```

---

