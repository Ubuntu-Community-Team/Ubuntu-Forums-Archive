---
title: "Seeing the network, but not connecting"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by Polar Bear64 on 2009-03-15
Hi

I've managed to get the drivers working on the usb netgear that connects to my computer. I can now see other networks including my own, but I am unable to connect to my network. Is there anything I should be doing?

---

### Post by Crafty Kisses on 2009-03-15
What are the results of the following commands?
```
lsusb
lspci
lshw -C network
ifconfig
iwconfig
```

---

### Post by Polar Bear64 on 2009-03-15
Hi

When I type in the following commands I get the following results:

lsusb
Bus 004 Device 004: ID 08bd:1100 Citizen Watch Co., Ltd X1-USB Floppy
Bus 004 Device 003: ID 55aa:b012 OnSpec Electronic, Inc. Mitsumi FA402M 8-in-2 Card Reader
Bus 004 Device 002: ID 55aa:0017 OnSpec Electronic, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:262a Pixart Imaging, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1385:4250 Netgear, Inc WG111T
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:11:11:c3:37:69
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:6c:36:63:6a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netwg11t driverversion=1.53+NETGEAR,10/15/2004,1.0.1.10 multicast=yes wireless=IEEE 802.11g
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 4
       logical name: pan0
       serial: 7a:e3:3f:e1:54:80
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:11:c3:37:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:6c:36:63:6a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:108 Mb/s   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

Hope this helps

---

### Post by Crafty Kisses on 2009-03-15
Did you install the drivers through ndiswrapper?

---

### Post by Polar Bear64 on 2009-03-15
not sure, as I've tried so many things.

If look under administration windows wireless divers I have
athfmwdl which says hardware present no.
netwg11t which says hardware present yes.

---

### Post by Crafty Kisses on 2009-03-16
Hmmm, well what are the results of the following command?
```
ndiswrapper -l
```

---

### Post by ugm6hr on 2009-03-17
This might help: [http://garethrwhite.wordpress.com/2009/02/05/netgear-wg111t-ubuntu/](http://garethrwhite.wordpress.com/2009/02/05/netgear-wg111t-ubuntu/)

---

### Post by stepen on 2009-03-24
I have exactly same issue with wg111t usb dongle adapter. I installed ndiswrapper, then I get the athfmwdl - driver's present
netwg11t - driver's present,

I can use Network-manager or WICD see the available networks, but I failed to connect to the network with WPA/WPA2 setting in router.

1 scene: Network manager keep ask me the password, i input the passphrase, it will convert to hex which same to what i can get with online WPA converter 

2 scene: I tried network manager with unsecure network, still not working, and after couple of try, the wireless network will disappearred from available network list, no matter if i refresh the list 

3 scene: I tried WICD with WPA/WPA2 router, won't work and will freeze the system

---

### Post by Polar Bear64 on 2009-04-05
Hi

ndiswrapper -l

athfmwdl : driver installed
netwg11t : driver installed
	device (1385:4250) present

---

### Post by Polar Bear64 on 2009-04-10
Hi Codename

When I type in

ndiswrapper -l

I get

athfmwdl : driver installed
netwg11t : driver installed
	device (1385:4250) present

---

