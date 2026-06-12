---
title: "Gateway computer won't connect"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by fbp90crx on 2009-06-07
I just installed ubuntu on a new partition on my desktop. The computer is a Gateway GT5622 ( [http://support.gateway.com/s/PC/R/10...4733Rsp2.shtml](http://support.gateway.com/s/PC/R/10...4733Rsp2.shtml) ) and the installation went smooth and fine but when I booted into it, it won't connect to the internet, is there a driver that didn't load or something I have to do manually?

---

### Post by Crafty Kisses on 2009-06-07
I clicked the link you provided and it doesn't work. So first you need to open up a Terminal, and run the following commands:
```
lspci
lsusb
ifconfig
iwconfig
lshw -C network
```That will tell me some information I need to know to help you further with your problem. Once I have the information I need I will try and help you.

---

### Post by fbp90crx on 2009-06-07
[http://support.gateway.com/s/PC/R/1014733R/1014733Rnv.shtml](http://support.gateway.com/s/PC/R/1014733R/1014733Rnv.shtml)
that link should work, and I'll boot into ubuntu and try to get you that info real quick

---

### Post by fbp90crx on 2009-06-07
ok this is what I got, in order of the way you asked.

```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
02:02.0 Communication controller: Conexant Systems, Inc. Device 2f40

```

```
Bus 001 Device 005: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 004: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 001 Device 003: ID 04b8:0838 Seiko Epson Corp. CX7300/CX7400/DX7400
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0461:4d16 Primax Electronics, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
eth0      Link encap:Ethernet  HWaddr 00:19:21:3d:25:49  
          inet6 addr: fe80::219:21ff:fe3d:2549/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4230 (4.2 KB)
          Interrupt:254 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```

```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:19:21:3d:25:49
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 4
       logical name: pan0
       serial: 46:51:42:ff:22:f5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by Iowan on 2009-06-07
I presume you're trying to get IP address via DHCP... Although my luck fixing other people's problem with [this]("http://ubuntuforums.org/showthread.php?t=1156441") solution is dwindling, I'll offer it - just in case.

---

### Post by alphacrucis2 on 2009-06-07
No IPV4 address for eth0. What does this say:


```
sudo ethtool eth0
```

---

### Post by fbp90crx on 2009-06-07
```
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes

```

---

### Post by alphacrucis2 on 2009-06-07
> **fbp90crx said:**
> ```
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes

```

Nothing physically wrong then. If you are running Jaunty or Intrepid you should see the network manager icon somewhere at the right hand end of the bar at the top of the screen. If you right click it, has it got enable networking ticked? Also select Edit Connections. Under the Wired tab it should list Auto eth0. Try selecting that and hit the edit button (will ask for password). Check under the IPv4 Settings tab that the method is set to Automatic (DHCP)

---

### Post by fbp90crx on 2009-06-08
> **alphacrucis2 said:**
> Nothing physically wrong then. If you are running Jaunty or Intrepid you should see the network manager icon somewhere at the right hand end of the bar at the top of the screen. If you right click it, has it got enable networking ticked? Also select Edit Connections. Under the Wired tab it should list Auto eth0. Try selecting that and hit the edit button (will ask for password). Check under the IPv4 Settings tab that the method is set to Automatic (DHCP)

I've already tried this earlier and it didn't work

---

### Post by fbp90crx on 2009-06-09
Is there a solution to this? I'd like to be able to actually use Ubuntu.

---

### Post by Iowan on 2009-06-09
What's in your */etc/dhcp3.dhclient.conf*?

---

### Post by fbp90crx on 2009-06-10
> **Iowan said:**
> What's in your */etc/dhcp3.dhclient.conf*?
this was in the dhclient.conf
```
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope, interface-mtu,
	rfc3442-classless-static-routes, ntp-servers;
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

```

---

### Post by fbp90crx on 2009-06-10
Nothing yet? lol I'm tired of using windows

---

### Post by fbp90crx on 2009-06-10
Bump

---

### Post by Iowan on 2009-06-10
Rule of thumb is that one bump/day is plenty...
Although I'm losing confidence in it's cure-all properties, see if [this]("http://ubuntuforums.org/showthread.php?t=1156441") one helps.

---

### Post by fbp90crx on 2009-06-10
> **Iowan said:**
> Rule of thumb is that one bump/day is plenty...
Although I'm losing confidence in it's cure-all properties, see if [this]("http://ubuntuforums.org/showthread.php?t=1156441") one helps.
I don't mean to overbump, its just that without the internet ubuntu is vitually pointless, so I've had it running for almost a week with no solution and havn't been ablt to do anything with it.
Ill give that thread a shot tho, thanks

---

### Post by fbp90crx on 2009-06-11
Iowan, I tried to do what you showed me, it was kinda hard to understand exactly what I needed to do, but whatever I did, didn't work.

---

