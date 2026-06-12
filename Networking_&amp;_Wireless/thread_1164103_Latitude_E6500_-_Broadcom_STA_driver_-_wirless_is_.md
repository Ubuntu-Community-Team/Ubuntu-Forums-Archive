---
title: "Latitude E6500 - Broadcom STA driver - wirless is disabled"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by mcd999 on 2009-05-19
I have a Dell Latitude E6500, and am trying to get wireless using the Broadcom STA driver. At one point I did have wireless, and am showing several wireless network (work, home, hotel) in my System > Preferences > Network Configuration, wireless tab.

But clicking on the network icon now shows "Wireless is disabled".  
  
When it stopped working, I downloaded the Broadcom STA driver. It is enableed an currently in use, as shown below:

System > Hardware Drivers shows

Broadcom STA Wireless Driver

"This driver is activated and currently in use"

The driver's name is "wl". 

Here is some more output:

$lspci

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
03:01.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

$lsusb

Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0a5c:5800 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


lspci -nn | grep -i broadcom

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)



$ifconfig

eth0      Link encap:Ethernet  HWaddr 00:21:70:ef:de:18  
          inet addr:192.168.1.189  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:feef:de18/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30460 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37068381 (37.0 MB)  TX bytes:2747713 (2.7 MB)
          Memory:f6ae0000-f6b00000 

eth1      Link encap:Ethernet  HWaddr 00:24:2b:81:a5:17  
          inet6 addr: fe80::224:2bff:fe81:a517/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

$iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.


$lsmod | grep wl

wl                   1080212  0 
ieee80211_crypt        13572  2 ieee80211_crypt_tkip,wl


$ dmesg | grep -i broadcom
[   13.601813] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.12

$  sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:21:70:ef:de:18
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=1.7-7 ip=192.168.1.189 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=1GB/s
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:24:2b:81:a5:17
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: be:a9:ba:c3:7e:37
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


$lsb_release -d
Description:    Ubuntu 8.10


$ uname -mr
2.6.27-11-generic i686

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...    


any help much appreciated!

---

### Post by superprash2003 on 2009-05-19
post output of **sudo iwlist scanning**

---

### Post by mcd999 on 2009-05-19
Right: 

 sudo iwlist scanning
 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

pan0      Interface doesn't support scanning.

---

### Post by mcd999 on 2009-05-19
Got it, from this thread:

[http://ubuntuforums.org/showthread.php?p=7308418#post7308418](http://ubuntuforums.org/showthread.php?p=7308418#post7308418)

If anyone else has a greyed out or unmanaged device in Network Manager its simply because you added the configuration to /etc/network/interfaces. Network manager looks there and if there is configuration data it leaves the device alone. If there is no configuration Network Manager will configure (¨manage¨) the device for you.

TO FIX:
remove the added lines from /etc/network/interfaces so all thats left is:

auto lo
iface lo inet loopback

Restart your computer and Network Manager will allow you to use your devices again ;)

Thanks! Your question on the scanning gave me something to latch onto for a search.

---

