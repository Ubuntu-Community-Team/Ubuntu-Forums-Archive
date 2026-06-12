---
title: "Network went down and can not connect now"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by mumblehappyfeet on 2009-05-12
Have a dual boot system and was going to get rid of winxp, but the internet stopped working on Ubuntu. It used to work seamless till a couple of days ago and now it doesnt....tried everything and hence this plea for help......

Appreciate help


root@ubuntu:/home/xx#  /etc/init.d/networking restart
 * Reconfiguring network interfaces...     

**After Reconfig**
root@ubuntu:/home/xx# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:76:4e:2f:3d  
          inet6 addr: fe80::20c:76ff:fe4e:2f3d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20660 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1475194 (1.4 MB)  TX bytes:10653 (10.6 KB)
          Interrupt:23 Base address:0x4500 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:524362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:524362 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26288144 (26.2 MB)  TX bytes:26288144 (26.2 MB)
                  

[B]This is the log file that i get
Log File[/B] 

May 13 07:27:33 ubuntu pppd[4704]: Plugin rp-pppoe.so loaded.
May 13 07:27:33 ubuntu pppd[4704]: RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
May 13 07:27:33 ubuntu pppd[4704]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
May 13 07:27:33 ubuntu pppd[4704]: pppd 2.4.5 started by root, uid 0
May 13 07:27:33 ubuntu pppd[4704]: PPP session is 161
May 13 07:27:33 ubuntu pppd[4704]: Connected to 00:1a:64:c1:09:5a via interface eth0
May 13 07:27:33 ubuntu pppd[4704]: Using interface ppp0
May 13 07:27:33 ubuntu pppd[4704]: Connect: ppp0 <--> eth0
May 13 07:27:42 ubuntu pppd[4704]: CHAP authentication failed: I don't like you.  Go 'way.
May 13 07:27:42 ubuntu pppd[4704]: Connection terminated.
May 13 07:27:42 ubuntu pppd[4704]: Exit.


**Added this line...**

sudo nano /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp


My Windows setting is
PPoE
Obtain IP Automatically
Obtain DNS server address automatically

---

### Post by mumblehappyfeet on 2009-05-12
**_Big problem now network is disabled :_**


**dmesg | grep eth1**

xx@ubuntu:~$ dmesg | grep eth0
[    3.546472] eth0: VIA Rhine II at 0xcfffb500, 00:0c:76:4e:2f:3d, IRQ 23.
[    3.547182] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[   16.114042] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   26.192008] eth0: no IPv6 routers present

**lspci**

xx@ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev 01)
00:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)


**lshw -C network**

xx@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:0c:76:4e:2f:3d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ee:30:ea:89:f9:f1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


**route**

xx@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0


**If Config**

xx@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:76:4e:2f:3d  
          inet6 addr: fe80::20c:76ff:fe4e:2f3d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12042 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:877524 (877.5 KB)  TX bytes:10782 (10.7 KB)
          Interrupt:23 Base address:0x4500 

eth0:avahi Link encap:Ethernet  HWaddr 00:0c:76:4e:2f:3d  
          inet addr:169.254.3.208  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:23 Base address:0x4500 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4192 (4.1 KB)  TX bytes:4192 (4.1 KB)

---

### Post by Iowan on 2009-05-13
Try commenting out the two eth0 lines:```
auto lo
iface lo inet loopback
#auto eth0
#iface eth0 inet dhcp

```Though it *should work, NM can get a li'l testy...*

---

