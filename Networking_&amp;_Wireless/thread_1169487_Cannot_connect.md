---
title: "Cannot connect"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by soliddiesel on 2009-05-25
hi, i just installed Ubuntu 9.04 Jaunty Jakalop,  on my AMD Athlon 3200+ 64 bit, Asus board, with built in LAN card and another card for local area, there is no problem with the hardware because i can use it on Vista Ultimate, Oh and yes i have dual OS, my cable modem is  SB5101 Surf Board.

Everything is coo, working A ok! but i cannot connect to the net!
last time i used Ubuntu! it was so seamless!! it kicked in windows face!!
and now i feel" its all coming back to me now...." ( all credits for this copy right song goes to Ms Celine Dion) no infringement intended!!
so plz guys!! if any one can come up with a solution!!!
by the way im posting the results of 2 commands i ran to check the network!! i hope some one can figure it out!!
 

ifconfig -a
sudo lshw -C network
-----------------------------


owais@Athlon64:~$ ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:e0:4d:84:9a:48  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:5 Base address:0xe800 



eth1      Link encap:Ethernet  HWaddr 00:18:f3:0c:80:68  

          inet6 addr: fe80::218:f3ff:fe0c:8068/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:26863 overruns:0 frame:0

          TX packets:0 errors:1 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:11 Base address:0xe400 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:36 errors:0 dropped:0 overruns:0 frame:0

          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:2672 (2.6 KB)  TX bytes:2672 (2.6 KB)



pan0      Link encap:Ethernet  HWaddr 1e:31:19:8c:28:09  

          BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



owais@Athlon64:~$ sudo lshw -C network

  *-network:0             

       description: Ethernet interface

       product: RTL-8139/8139C/8139C+

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: c

       bus info: pci@0000:00:0c.0

       logical name: eth0

       version: 10

       serial: 00:e0:4d:84:9a:48

       size: 10MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s

  *-network:1

       description: Ethernet interface

       product: VT6102 [Rhine-II]

       vendor: VIA Technologies, Inc.

       physical id: 12

       bus info: pci@0000:00:12.0

       logical name: eth1

       version: 7c

       serial: 00:18:f3:0c:80:68

       size: 100MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s

  *-network DISABLED

       description: Ethernet interface

       physical id: 1

       logical name: pan0

       serial: 1e:31:19:8c:28:09

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

owais@Athlon64:~$

---

### Post by RedSingularity on 2009-05-27
Type "lspci" in the terminal and post.

---

### Post by superprash2003 on 2009-05-27
is this wired?
in your terminal type the following commands and post output
1)sudo dhclient eth1
2)sudo dhclient eth0

---

### Post by soliddiesel on 2009-05-27
> **Shadow121 said:**
> Type "lspci" in the terminal and post.
owais@Athlon64:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. Device 6290
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M890CE/K8N890CE [Chrome 9] (rev 11)
04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
owais@Athlon64:~$

---

### Post by soliddiesel on 2009-05-27
> **superprash2003 said:**
> is this wired?
in your terminal type the following commands and post output
1)sudo dhclient eth1
2)sudo dhclient eth0
yes  this is a wired connection through surf board cable modem, on eth1
owais@Athlon64:~$ sudo dhclient eth1

[sudo] password for owais: 

Internet Systems Consortium DHCP Client V3.1.1

Copyright 2004-2008 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/eth1/00:18:f3:0c:80:68

Sending on   LPF/eth1/00:18:f3:0c:80:68

Sending on   Socket/fallback

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18

No DHCPOFFERS received.

No working leases in persistent database &#8211; sleeping.



2)sudo dhclient eth0

owais@Athlon64:~$ sudo dhclient eth0
[sudo] password for owais: 
There is already a pid file /var/run/dhclient.pid with pid 3609
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:e0:4d:84:9a:48
Sending on   LPF/eth0/00:e0:4d:84:9a:48
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping

---

### Post by Iowan on 2009-05-27
No guarantee [this]("http://ubuntuforums.org/showthread.php?t=1156441") will fix your problem, but it fixed mine.
I presume eth0 and eth1 get addresses from different DHCP servers?

---

### Post by soliddiesel on 2009-05-29
> **Iowan said:**
> No guarantee [this]("http://ubuntuforums.org/showthread.php?t=1156441") will fix your problem, but it fixed mine.
I presume eth0 and eth1 get addresses from different DHCP servers?

Tried it but still not working!!  should i remove the comment? or leave it.

By the way i personally think there is something with DHCP, cause i tried to trick it by first connecting the modem to Windows, got an auto-assaigned IP, DNS and gateway, manually entered those in my connection settings! and It shows connected!! ( well ofcourse i connected the wire to Ubuntu machine) its not working because ofcourse went i disconnected it, the DHCP refreshes the IP and default gateway, but the thing is, it got connected it was able to communicate! but upto what level ( I was not able to browse), and why!! i dont know in Linux how to find that out.
I tried to connect the modem via USB! but........:S Ubuntu didnot pick it up!! sorry if im missing something! but is Ubuntu not supposed to be plug and play! 
it was then i noticed my USB stick is also not being detected! is it an issue or just because i didnot update Ubuntu its not picking it up.

---

### Post by Habboblob on 2009-05-29
Mmmm. This is hard. We need to think bud. And it doesn't matter if you have a dual boot.

My one question is, could it be that your other operating system is using the connection, and not letting ubuntu access it. As my old desktop with Windows Vista always had it's connection idle, even when the computer wasn't even on, the eternal card lights were flashing.

---

### Post by soliddiesel on 2009-05-29
> **Habboblob said:**
> Mmmm. This is hard. We need to think bud. And it doesn't matter if you have a dual boot.

My one question is, could it be that your other operating system is using the connection, and not letting ubuntu access it. As my old desktop with Windows Vista always had it's connection idle, even when the computer wasn't even on, the eternal card lights were flashing.

Those lights flash to listen to Wake on LAN calls, or to find DHCP, so technically the connection is not being used, secondly i used the connection on another machine, ( my laptop) when i tried to get ip address for manual settings, so once  wire was DC OS cannot stay connected to that connection. 
Come on guys!! work something Out!!

---

### Post by superprash2003 on 2009-05-29
post contents of /etc/dhcp3/dhclient.conf

---

### Post by soliddiesel on 2009-05-30
> **superprash2003 said:**
> post contents of /etc/dhcp3/dhclient.conf
=================================
# Configuration file for /sbin/dhclient, which is included in Debian's
#    dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#    man page for more information about the syntax of this file
#    and a more comprehensive list of the parameters understood by
#    dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#    not leave anything out (like the domain name, for example), then
#    few changes must be made to this file, if any.
#

#      option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    netbios-name-servers, netbios-scope, interface-mtu,
     ntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

---

### Post by soliddiesel on 2009-05-30
why can i connect giving bogus IP and subnet mask!! i mean the status shows connected, but actually there is no data flow. :S

---

### Post by superprash2003 on 2009-05-31
ok i see that you have already tried Iowan's suggestion..which interface do you use to connect from eth0,eth1 and pan0?

---

### Post by soliddiesel on 2009-06-01
> **superprash2003 said:**
> ok i see that you have already tried Iowan's suggestion..which interface do you use to connect from eth0,eth1 and pan0?
i use eth1 to connect to Internet, and eth0 for my local lan. By the way my eth0 shows connected to local lan, where i configured IP manually, but it cannot detect others window machines on the lan, i'll solve that later!! ( i tried making it the default gateway and even by making it a user connecting to other machine on lan)

---

### Post by superprash2003 on 2009-06-01
there seems to be some conflict between the interfaces.. you could try bringing down all other interfaces other than the one you currently want to use .. and then try.. the command to bring down eth0 is **sudo ifdown eth0 **.. use this for whichever interface you wish to bring down

---

### Post by Iowan on 2009-06-01
For later: the manual configuration may need to have DNS servers and gateway manually set (since DHCP doesn't provide them). Is manual configuration via NM or */etc/network/interfaces*?

---

### Post by soliddiesel on 2009-06-02
> **Iowan said:**
> For later: the manual configuration may need to have DNS servers and gateway manually set (since DHCP doesn't provide them). Is manual configuration via NM or */etc/network/interfaces*?


i assaigned the same values as i do to connect any windows machine, 
ip= 192.168.0.2
subnet mask: 225.225.225.0
default gateway: 192.168.0.1
DNS Server: 192.168.0.1

Now my laptop has the ip 192.168.0.1 running XP
any other windows machine connects to it, Via switch
so i expect ubuntu also to connect via switch with above manual settings

---

### Post by soliddiesel on 2009-06-02
> **superprash2003 said:**
> there seems to be some conflict between the interfaces.. you could try bringing down all other interfaces other than the one you currently want to use .. and then try.. the command to bring down eth0 is **sudo ifdown eth0 **.. use this for whichever interface you wish to bring down


it couldnot bring down any interface, because it says it couldnot find any interface by name of eth0
i even tried " Auto eth0" no use!! :(
maybe there is some mistake in this command
well the command gets executed, but it cannot find the interface....i tried other ones also
like eth1

---

### Post by soliddiesel on 2009-06-03
owais@Athlon64:~$ sudo ifdown "Auto eth0"

ifdown: interface Auto eth0 not configured

owais@Athlon64:~$ sudo ifdown "eth0"

ifdown: interface eth0 not configured

owais@Athlon64:~$ sudo ifdown eth0

ifdown: interface eth0 not configured

---

### Post by superprash2003 on 2009-06-03
post output of ifconfig again.. also post contents of /etc/network/interfaces

---

### Post by soliddiesel on 2009-06-04
> **superprash2003 said:**
> post output of ifconfig again.. also post contents of /etc/network/interfaces



owais@Athlon64:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:84:9a:48  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe84:9a48/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0xe800 

eth1      Link encap:Ethernet  HWaddr 00:18:f3:0c:80:68  
          inet6 addr: fe80::218:f3ff:fe0c:8068/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:11987 overruns:0 frame:0
          TX packets:0 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2765 (2.7 KB)  TX bytes:2765 (2.7 KB)

owais@Athlon64:~$

=============interfaces===========

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

---

### Post by soliddiesel on 2009-06-07
Come on people!! where r ur skills!!!
resolve this issue.

---

### Post by superprash2003 on 2009-06-08
now your eth0 has an ip 192.168.0.7 , hasnt it been resolved?are you able to access your router?

---

### Post by soliddiesel on 2009-06-08
> **superprash2003 said:**
> now your eth0 has an ip 192.168.0.7 , hasnt it been resolved?are you able to access your router?

eth0 is my local lan! with manual assaigned IP.

what is not getting IP from DHCP is eth1! 
(I made a connection by name of WorldCall on eth1 also)

---

### Post by soliddiesel on 2009-06-08
I read on a thread some one talking about removing network manager!! and that it interfares with getting IP!! :S

is this a known issue!! im using Jaunty (9.04)
should i try? 
I am not very good with terminal commands so i dont want to get stuck without a GUI Network Manager.

[http://ubuntuforums.org/showthread.php?t=1181516](http://ubuntuforums.org/showthread.php?t=1181516)

---

### Post by Iowan on 2009-06-08
Try putting your manual configuration (eth0) in **/etc/network/interfaces** and using Network Manager to configure eth1 for DHCP.  It *should* work via NM... but let's see if we can get *something* to connect.

---

