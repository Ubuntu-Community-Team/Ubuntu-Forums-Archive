---
title: "Unable to DHCP After Installing Jaunty RC AMD64"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by edwin11 on 2009-04-18
Hi all,

My desktop is connected to an ADSL modem/router via WIRED Ethernet. Previously, using Intrepid (i386), there wasn't a problem.

Yesterday i installed (clean) Jaunty RC (AMD64), and have been unable to get a lease from the modem/router via DHCP.

Another thing to add, when i tested using the i386 version (also of Jaunty RC, using live CD), and there is no such issue.


This is my [FONT="Courier New"]ifconfig[/FONT]:

```
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:28:6c:59  
          inet6 addr: fe80::21b:fcff:fe28:6c59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:407 errors:0 dropped:0 overruns:1 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27451 (27.4 KB)  TX bytes:0 (0.0 B)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```

This are the lines in [FONT="Courier New"]dmesg | grep eth0[/FONT]:

```
[    3.959915] skge eth0: addr 00:1b:fc:28:6c:59
[   18.206080] skge eth0: enabling interface
[   18.209765] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.929597] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
[   19.930197] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   30.308015] eth0: no IPv6 routers present
```


This is the [FONT="Courier New"]syslog tail[/FONT] while trying to DHCP (click on the NetworkManager applet and click on "auto eth0"):

```
Apr 18 22:33:22 mydesktop kernel: [  867.745023] device eth0 entered promiscuous mode
Apr 18 22:33:26 mydesktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
Apr 18 22:33:26 mydesktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Apr 18 22:33:26 mydesktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 18 22:33:26 mydesktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr 18 22:33:26 mydesktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 18 22:33:26 mydesktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr 18 22:33:26 mydesktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr 18 22:33:26 mydesktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Apr 18 22:33:26 mydesktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr 18 22:33:26 mydesktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr 18 22:33:26 mydesktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr 18 22:33:26 mydesktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr 18 22:33:26 mydesktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Apr 18 22:33:26 mydesktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Apr 18 22:33:26 mydesktop NetworkManager: <info>  dhclient started with pid 3570 
Apr 18 22:33:26 mydesktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr 18 22:33:26 mydesktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Apr 18 22:33:26 mydesktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Apr 18 22:33:26 mydesktop dhclient: All rights reserved.
Apr 18 22:33:26 mydesktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 18 22:33:26 mydesktop dhclient: 
Apr 18 22:33:26 mydesktop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit 
Apr 18 22:33:26 mydesktop dhclient: Listening on LPF/eth0/00:1b:fc:28:6c:59
Apr 18 22:33:26 mydesktop dhclient: Sending on   LPF/eth0/00:1b:fc:28:6c:59
Apr 18 22:33:26 mydesktop dhclient: Sending on   Socket/fallback
Apr 18 22:33:27 mydesktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 18 22:33:30 mydesktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr 18 22:33:36 mydesktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr 18 22:33:49 mydesktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr 18 22:34:02 mydesktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Apr 18 22:34:12 mydesktop NetworkManager: <info>  Device 'eth0' DHCP transaction took too long (>45s), stopping it. 
Apr 18 22:34:12 mydesktop NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 3570 
Apr 18 22:34:12 mydesktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Apr 18 22:34:12 mydesktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
Apr 18 22:34:12 mydesktop NetworkManager: <info>  (eth0): device state change: 7 -> 9 
Apr 18 22:34:12 mydesktop NetworkManager: <info>  Marking connection 'Auto eth0' invalid. 
Apr 18 22:34:12 mydesktop NetworkManager: <info>  Activation (eth0) failed. 
Apr 18 22:34:12 mydesktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete. 
Apr 18 22:34:12 mydesktop NetworkManager: <info>  (eth0): device state change: 9 -> 3 
Apr 18 22:34:12 mydesktop NetworkManager: <info>  (eth0): deactivating device (reason: 0). 
Apr 18 22:34:22 mydesktop kernel: [  927.969018] device eth0 left promiscuous mode
```

* promiscuity is probably due to running tcpdump (below).


And this is the [FONT="Courier New"]tcpdump -n -i eth0 -s 0 -vv[/FONT] for the same DHCP requests:

```
tcpdump: WARNING: eth0: no IPv4 address assigned
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
22:33:27.000648 IP (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328) 0.0.0.0.68 > 255.255.255.255.67: [udp sum ok] BOOTP/DHCP, Request from 00:1b:fc:28:6c:59, length 300, xid 0xe0708c51, Flags [none] (0x0000)
	  Client-Ethernet-Address 00:1b:fc:28:6c:59
	  Vendor-rfc1048 Extensions
	    Magic Cookie 0x63825363
	    DHCP-Message Option 53, length 1: Discover
	    Hostname Option 12, length 10: "mydesktop"
	    Parameter-Request Option 55, length 13: 
	      Subnet-Mask, BR, Time-Zone, Default-Gateway
	      Domain-Name, Domain-Name-Server, Option 119, Hostname
	      Netbios-Name-Server, Netbios-Scope, MTU, Classless-Static-Route
	      NTP
22:33:30.003041 IP (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328) 0.0.0.0.68 > 255.255.255.255.67: [udp sum ok] BOOTP/DHCP, Request from 00:1b:fc:28:6c:59, length 300, xid 0xe0708c51, secs 3, Flags [none] (0x0000)
	  Client-Ethernet-Address 00:1b:fc:28:6c:59
	  Vendor-rfc1048 Extensions
	    Magic Cookie 0x63825363
	    DHCP-Message Option 53, length 1: Discover
	    Hostname Option 12, length 10: "mydesktop"
	    Parameter-Request Option 55, length 13: 
	      Subnet-Mask, BR, Time-Zone, Default-Gateway
	      Domain-Name, Domain-Name-Server, Option 119, Hostname
	      Netbios-Name-Server, Netbios-Scope, MTU, Classless-Static-Route
	      NTP
22:33:36.003170 IP (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328) 0.0.0.0.68 > 255.255.255.255.67: [udp sum ok] BOOTP/DHCP, Request from 00:1b:fc:28:6c:59, length 300, xid 0xe0708c51, secs 9, Flags [none] (0x0000)
	  Client-Ethernet-Address 00:1b:fc:28:6c:59
	  Vendor-rfc1048 Extensions
	    Magic Cookie 0x63825363
	    DHCP-Message Option 53, length 1: Discover
	    Hostname Option 12, length 10: "mydesktop"
	    Parameter-Request Option 55, length 13: 
	      Subnet-Mask, BR, Time-Zone, Default-Gateway
	      Domain-Name, Domain-Name-Server, Option 119, Hostname
	      Netbios-Name-Server, Netbios-Scope, MTU, Classless-Static-Route
	      NTP
22:33:49.013109 IP (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328) 0.0.0.0.68 > 255.255.255.255.67: [udp sum ok] BOOTP/DHCP, Request from 00:1b:fc:28:6c:59, length 300, xid 0xe0708c51, secs 22, Flags [none] (0x0000)
	  Client-Ethernet-Address 00:1b:fc:28:6c:59
	  Vendor-rfc1048 Extensions
	    Magic Cookie 0x63825363
	    DHCP-Message Option 53, length 1: Discover
	    Hostname Option 12, length 10: "mydesktop"
	    Parameter-Request Option 55, length 13: 
	      Subnet-Mask, BR, Time-Zone, Default-Gateway
	      Domain-Name, Domain-Name-Server, Option 119, Hostname
	      Netbios-Name-Server, Netbios-Scope, MTU, Classless-Static-Route
	      NTP
22:34:02.002475 IP (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328) 0.0.0.0.68 > 255.255.255.255.67: [udp sum ok] BOOTP/DHCP, Request from 00:1b:fc:28:6c:59, length 300, xid 0xe0708c51, secs 35, Flags [none] (0x0000)
	  Client-Ethernet-Address 00:1b:fc:28:6c:59
	  Vendor-rfc1048 Extensions
	    Magic Cookie 0x63825363
	    DHCP-Message Option 53, length 1: Discover
	    Hostname Option 12, length 10: "mydesktop"
	    Parameter-Request Option 55, length 13: 
	      Subnet-Mask, BR, Time-Zone, Default-Gateway
	      Domain-Name, Domain-Name-Server, Option 119, Hostname
	      Netbios-Name-Server, Netbios-Scope, MTU, Classless-Static-Route
	      NTP
^C
5 packets captured
5 packets received by filter
0 packets dropped by kernel
```


Any advise/suggestion, please?



Thanks and Regards,
Edwin

---

### Post by edwin11 on 2009-04-18
Hi, anyone able to help, please?

---

### Post by DGortze380 on 2009-04-18
> **edwin11 said:**
> Hi, anyone able to help, please?

please post the output of 

```

cat /etc/networking/interfaces

```

---

### Post by edwin11 on 2009-04-19
Hi,

```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

hmm... there's only lo in there, no eth0, but i'm not sure if this is the problem, because:

- i configure the network using the NetworkManager applet.

- when i booted up to Jaunty RC i386 (live CD) to have a look, the /etc/network/interfaces file also only contains "lo" (content's exactly the same in fact), and networking's fine there.



Thanks and Regards,
Edwin

---

### Post by superprash2003 on 2009-04-19
post output of **sudo dhclient eth0**

---

### Post by edwin11 on 2009-04-23
Hi all,

After some troubleshooting and diagnosis, with help from fellow members of the Slugnet Mailing List, it is found that the problem lies with the device driver when using more than 3 GB of RAM. i'm using the motherboard M2A-MVP which contains the onboard ethernet Marvell 88E8001. This is the link that we found detailing the root cause: [http://kerneltrap.org/mailarchive/linux-netdev/2009/2/10/4944484](http://kerneltrap.org/mailarchive/linux-netdev/2009/2/10/4944484). It also contains the workaround patch (i did not apply it though).

i've also posted the troubleshooting process we went through on my blog here: [http://hello-world-2-0.blogspot.com/2009/04/ethernet-card-issue-when-using-amd-64.html](http://hello-world-2-0.blogspot.com/2009/04/ethernet-card-issue-when-using-amd-64.html).

Hopefully this would help someone else facing the same issue.



Thanks and Regards,
Edwin

---

