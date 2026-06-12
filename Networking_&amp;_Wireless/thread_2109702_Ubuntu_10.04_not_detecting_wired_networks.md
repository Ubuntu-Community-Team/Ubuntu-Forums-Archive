---
title: "Ubuntu 10.04 not detecting wired networks"
date: 2013-01-28
forum: Networking &amp; Wireless
---

### Post by RxBoo on 2013-01-28
Hi, 

My ubuntu 10.04 install can only detect wireless networks and not wired connections. I have a dual boot machine and there is no problem detecting wired networks on the windows boot but not the ubuntu version. Is there any suggestions on how to fix this?

I thought it might help to post the output from '
iconfig -a'


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1436 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:111704 (111.7 KB)  TX bytes:111704 (111.7 KB)

pan0      Link encap:Ethernet  HWaddr 42:9d:20:58:35:44  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 74:de:2b:f5:93:9a  
          inet addr:134.171.185.137  Bcast:134.171.185.255  Mask:255.255.255.0
          inet6 addr: fe80::76de:2bff:fef5:939a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7492 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6112896 (6.1 MB)  TX bytes:1167281 (1.1 MB)



cheers.

---

### Post by Warren Hill on 2013-01-28
Given that 10.04 will stop being supported in April this year; just a few weeks from now; I wouldn't bother.  I would make sure I had good backups and do a clean install of 12.04.
Not an upgrade as if there are problems with your network settings they may be copied into the upgrade.

However, If you don't want to upgrade then open a terminal and with a LAN cable plugged in give us the output of the following terminal commands

----------------------------------------------------------------------------------------------------
sudo lshw -C network; ifconfig; route -n; cat /etc/network/interfaces
----------------------------------------------------------------------------------------------------

Enter password when requested.  You may need to unplug the LAN cable to get Wifi back so you can post the results

---

### Post by RxBoo on 2013-01-28
The results of ```
 sudo lshw -C network; ifconfig; route -n; cat /etc/network/interfaces 
``` is: 

>   *-network UNCLAIMED     
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:c4800000-c481ffff memory:c482a000-c482afff ioport:3060(size=32)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 74:de:2b:f5:93:9a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:c2600000-c260ffff
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2695 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2695 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:213654 (213.6 KB)  TX bytes:213654 (213.6 KB)

wlan0     Link encap:Ethernet  HWaddr 74:de:2b:f5:93:9a  
          inet6 addr: fe80::76de:2bff:fef5:939a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:22114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24800 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15740864 (15.7 MB)  TX bytes:4090813 (4.0 MB)

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
auto lo
iface lo inet loopback


---

### Post by Warren Hill on 2013-01-28
The problem is here
```
*-network UNCLAIMED     
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:c4800000-c481ffff memory:c482a000-c482afff ioport:3060(size=32)
```

UNCLAIMED means there is no driver claiming it

Try
```
sudo apt-get install linux-backports-modules-lucid
```

Enter password when requested and reboot to test.

---

### Post by RxBoo on 2013-01-28
Thanks for finding the root of the problem. 
However the package linux-backports-modules-lucid wasn't found. Are there any other options I could try?

---

### Post by Warren Hill on 2013-01-28
Try looking here
[http://askubuntu.com/questions/113794/how-do-i-install-the-ethernet-drivers-in-ubuntu-10-04](http://askubuntu.com/questions/113794/how-do-i-install-the-ethernet-drivers-in-ubuntu-10-04)

---

### Post by RxBoo on 2013-01-28
Have tried ```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
``` and still get the * - network UNCLAIMED response. 

In some of the other post I saw that the output from ```
lspci
``` might help. This is :

lspci
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0126 (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Device 1503 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b4)
00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b4)
00:1c.5 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 6 (rev b4)
00:1c.6 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev b4)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1c49 (rev 04)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04)
01:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 04)
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
05:00.0 USB Controller: NEC Corporation Device 0194 (rev 04)



I don't fancy upgrading the operating system as I have several specialized programs, so would like to fix this if possible. 

Cheers.

---

### Post by collisionystm on 2013-01-28
Go here.

[http://www.intel.com/support/network/sb/CS-012904.htm](http://www.intel.com/support/network/sb/CS-012904.htm)

Instructions for identifying your adapter on linux and then you can search intel for the proper drivers. They do support linux. Your problem is intel always packages their drivers into the Linux Kernel. The newer the kernel the newer/more drivers you have. 10.04 is obviously using a very old kernel, therefore it has old outdated drivers.

Good luck!

P.S.

if you want to keep 10.04, look into updating your kernel to something more recent.

[http://www.howopensource.com/2011/08/how-to-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/](http://www.howopensource.com/2011/08/how-to-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/)

---

