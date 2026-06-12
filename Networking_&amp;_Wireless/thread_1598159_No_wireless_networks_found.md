---
title: "No wireless networks found"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by daniel.standage on 2010-10-16
I installed Lubuntu yesterday on an older Dell laptop and the installation went fine. The only thing not working after the installation was the wireless. After hours of searching, I was finally about to get it to recognize the wireless card, see wireless networks, and connect successfully by running these commands.

```
sudo apt-get install pcmciautils
sudo apt-get install wicd
sudo apt-get remove network-manager network-manager-gnome
sudo apt-get purge network-manager network-manager-gnome
```I was relieved to have solved the issue. However, when I came home, the computer did not recognize my wireless router (Wicd says "No wireless networks found"). I've looked around some more for help, but I don't even know where to start now. Any ideas?

Thanks.

Here are some details.

 1. Dell Latitude C510/C610 (can' tell which one)
 2. Wireless info 
```
standage@standage-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
standage@standage-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
 3. Interfaces
```
standage@standage-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:5b:e2:fe:cc  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fee2:fecc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1597 errors:0 dropped:0 overruns:0 frame:0
          TX packets:985 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1675236 (1.6 MB)  TX bytes:141828 (141.8 KB)
          Interrupt:11 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:276 (276.0 B)  TX bytes:276 (276.0 B)

standage@standage-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:""  
          Mode:Managed  Bit Rate:11 Mb/s   
          RTS thr:off   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
6. Network configuration ```
standage@standage-laptop:~$ sudo lshw -C network
[sudo] password for standage: 
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:e2:fe:cc
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.0.2 latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: irq:11 ioport:ec80(size=128) memory:f8fffc00-f8fffc7f memory:4c000000-4c01ffff(prefetchable)
  *-network
       description: TrueMobile 1150 Series PC Card
       product: Version 01.01
       vendor: Dell
       physical id: 0
       slot: Socket 2
       resources: irq:5
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:56:53:c0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b
```
7. Scan ```
standage@standage-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Network is down
```

---

### Post by cavalier911 on 2010-10-17
Go into WICD preferences,set the default wireless interface to eth1.You have a Hermes Lucent Agere wireless chip,there is an issue with new firmware which adds WPA security to orinoco_cs driver. 

This user was able to connect with WICD and leaving firmware in place: [http://ubuntuforums.org/showthread.php?t=1581170&page=2](http://ubuntuforums.org/showthread.php?t=1581170&page=2)

Problem is in most cases it breaks the wireless.If you can't get wireless
to work go to [http://ubuntuforums.org/showthread.php?t=1593250&page=3](http://ubuntuforums.org/showthread.php?t=1593250&page=3) thread #28 for directions on moving the firmware so the wireless card driver won't load it.

---

### Post by daniel.standage on 2010-10-18
I moved the firmware, but was still unable to locate my home wireless network. I then tried removing wicd and reinstalling NetworkManager, but NM cannot find the network either! Do you have any other suggestions?

Thanks.

---

### Post by cavalier911 on 2010-10-18
To conserve battery most laptops with builtin wireless have wireless adapter power switch.
Verify the wireless adapter hardware is turned on.
My Dell Inspirion E1505 has a led indicator and is switched on with Fn+F3 key combo.

Stop NetworkManager
```
sudo service  network-manager stop
```
Restart NetworkManager in debug mode
```
sudo NetworkManager --no-daemon
```
Post from this output where the connection process fails.
Post output from:
```
nm-tool
```
```
lsmod
```
```
iwlist scanning
```
```
iwconfig
```
```
dmesg | grep -e eth1 -e orinoco
```

---

