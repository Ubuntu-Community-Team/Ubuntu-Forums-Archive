---
title: "Wired connection to livebox not working - Help!"
date: 2011-05-23
forum: Networking &amp; Wireless
---

### Post by thesergeant on 2011-05-23
Dear all,

Can any body assist me to get my Ubuntu 11.04 back onto the internet?

I am using a livebox with two wired PCs. One windows and one Ubuntu. The Ubuntu machine used to work fine on the internet. I have not used it for some time, but having got it running again there is no wired connection - Ubuntu searches but comes up wired connection disconnected. I have checked the cable and that is fine I swapped the two cables over and it works fine on the Windows machine.

The cable in the livebox shows two constant lights. The green light does not flash though - it is constantly on - I beleive this means the connection is good but there is no data flow.

The Network manager applet shows only the auto ethernet, in edit mode there is no MAC address or anything else.

Please help me. I have been going round in circles without success.

---

### Post by thesergeant on 2011-05-23
Hope this assists in helping me:

~$ ifconfig 
eth1      Link encap:Ethernet  HWaddr 00:16:17:8c:77:b7  
          inet6 addr: fe80::216:17ff:fe8c:77b7/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:9112 (9.1 KB) 
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1057 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1057 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:131381 (131.3 KB)  TX bytes:131381 (131.3 KB) 


$ iwconfig 
lo        no wireless extensions. 

eth1      no wireless extensions. 

$ lspci 
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge 
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge 
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge 
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge 
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge 
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge 
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] 
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
 01:00.0 VGA compatible controller: nVidia Corporation NV34GL [Quadro FX 500/600 PCI] (rev  a1) 


$ dhclient 
Internet Systems Consortium DHCP Client V3.1.3 
Copyright 2004-2009 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/) 

can't create /var/lib/dhcp3/dhclient.leases: Permission denied 
SIOCSIFADDR: Permission denied 
SIOCSIFFLAGS: Permission denied 
SIOCSIFFLAGS: Permission denied 
Open a socket for LPF: Operation not permitted 


$ cat /var/log/dmesg | grep -i eth 
[    1.309631] eth0: VIA Rhine II at 0xfa001000, 00:16:17:8c:77:b7, IRQ 23. 
[    1.310338] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1. 
[   30.337080] udev[357]: renamed network interface eth0 to eth1 
[   31.559563] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1 


$ cat /etc/network/interfaces 
auto lo 
iface lo inet loopback

---

### Post by thesergeant on 2011-05-23
Additionally I have tried Ping. I get nothing either by name or by ip address.

---

### Post by thesergeant on 2011-05-23
To assist anyone else with this type of problem - I have finally resolved it.

I recently received the new Orange Livebox with the green lights to replace my old bigger livebox with red lights.

To enable port 2, which my Ubuntu machine was connected to you have to log in to the Livebox and disable Digital TV in the services section. 

I am now up and running ................ :-)

---

### Post by Phil Binner on 2011-07-17
Hi

Nice to know you think you have a solution,but I suspect it will rear it's ugly head again. I have had this problem intermittently for several weeks now. Usually re-booting the livebox fixes it temporarily, but by the morning it's down again. The problem is definitely with the livebox, because it can be fixed at the livebox for a while, but it only seems to affect Ubuntu. I can connect with Windows or Android, and my son's I phone doesn't have a problem.

The problem seems to be that the Livebox is a **** of ****. Orange is stopping giving them out, which is a shame if, like me, you use the second line to feed into a telephone switch and give you a proper 2 line telephone system.

If any of you technical wizards out there know what it is about Ubuntu that makes it more sensitive to router problems, then please pick up this thread. Particularly if there is a solution.

---

