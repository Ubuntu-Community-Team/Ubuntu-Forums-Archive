---
title: "Does ubuntu 12.04 support 802.11n draft ?"
date: 2012-06-11
forum: Networking &amp; Wireless
---

### Post by omega341991 on 2012-06-11
I would like to know whether ubuntu 12.04 support 802.11n draft? Because i only get 11b and 11g only
My NIC adapter supports 11a,b,g and n.
But i am not able to get 11n 


Please reply

---

### Post by roelforg on 2012-06-11
My 11.10 does so (if i plug in the 11n usb receiver, that is, the buildin one is a/b/g only), so 12.04 should do so too.
 
But look at it from the other side, do you get 11n in windows?
Keep in mind that your router needs to support 11n too.

---

### Post by omega341991 on 2012-06-11
My router supports 11n standards (checked in windows 7 ) and its working fine
I tried capturing packets using tcpdump and only 11g and 11b packets are captured. 11n packets are not captured (i can assure you that there are 11n packets on air as i checked with windows )

So does 12.04 support 11n transactions?

please reply

---

### Post by roelforg on 2012-06-11
Run the following commands and post their output:
```

iwlist scan
sudo ifconfig -a
sudo lshw -C network
sudo lspci
sudo lsusb
sudo tail /var/log/syslog
dmesg | tail
dmesg | grep -i eth

```

---

### Post by omega341991 on 2012-06-11
Here are the outputs of commands (btw i am using the wireless adapter shown as "wlan0"

root:~$ iwlist scan
[ code ]
lo        Interface doesn't support scanning.
eth1      Interface doesn't support scanning.
wlan0     No scan results
eth0      Interface doesn't support scanning.
[ code ]
=========================================================================
root:~$ ifconfig -a
 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5266 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5266 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:452310 (452.3 KB)  TX bytes:452310 (452.3 KB)

wlan0     Link encap:UNSPEC  HWaddr 00-21-A6-54-71-5C-33-30-00-00-00-00-00-00-00-00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4501 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2644188 (2.6 MB)  TX bytes:0 (0.0 B)

=============================================================================
root:~$ lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:40:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:fe:1d:5d:35
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=5751-v3.29a latency=0 link=no multicast=yes port=twisted pair
       resources: irq:17 memory:f0400000-f040ffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@0000:05:04.0
       logical name: eth1
       version: 10
       serial: 00:08:a1:97:27:9b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=172.20.34.39 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:1000(size=256) memory:f0501000-f05010ff

==================================================================================

root:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
05:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:09.0 CardBus bridge: Ricoh Co Ltd RL5c475
40:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)

===============================================================================
root:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0411:015d BUFFALO INC. (formerly MelCo., Inc.) WLI-UC-GN Wireless LAN Adapter [Ralink RT3070]

===============================================================================

root:~$ tail /var/log/syslog
Jun 11 13:52:30 user kernel: [336595.887063] device wlan0 entered promiscuous mode
Jun 11 13:52:34 user kernel: [336600.260567] device wlan0 left promiscuous mode

================================================================================

root:~$ dmesg | tail

[336595.887063] device wlan0 entered promiscuous mode
[336600.260567] device wlan0 left promiscuous mode

===============================================================================

hope all this info can help you to solve my problem

---

### Post by roelforg on 2012-06-11
In the future, wrap those outputs in [ code ] tags; that is much easier to read.
 
I noticed it's a realtek, can you check for any missing additional drivers (that should be system settings -> additional drivers) and install any outstanding updates.
Some wireless cards need propriatary drivers and it's against canonical policy to include them by default, you need to install them via additional drivers, it could be that the oss one doesn't support 11n yet.
 
If that didn't work either, you could see if you can find ubuntu drivers from the manufacturer directly, but those can be a pain to install (or flat out refuse to do so without some obscure patch; don't laugh, that really happened to me!).

---

### Post by omega341991 on 2012-06-11
< code >
There are no additional drivers to install. Btw is it possible that 12.04 doesnt support 11n transactions? How can i confirm?

</code >

---

### Post by roelforg on 2012-06-11
[http://ubuntuforums.org/showthread.php?t=1402802](http://ubuntuforums.org/showthread.php?t=1402802)
Try chili555's answer, i remember having to do that for a 54g usb receiver that, incidentally, has a similar chipset as yours (same driver) (yes, i have both 11n and 54g usb receivers).

---

### Post by omega341991 on 2012-06-11
Still no luck :( 
The fact that i don understand is that i am able to capture packets in both 11g and 11b modes using tcpdump. Its that only packets in 11n cant be captured ... If it works for 11b and g , it should work for 11n also na

---

