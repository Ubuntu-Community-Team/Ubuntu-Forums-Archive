---
title: "Ubuntu does not detect router, WIRED."
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by Nisstyre56 on 2009-06-25
Ubuntu just ceased to be able to detect my router. Running 9.04. (Jaunty?)

I have tried deleting and creating a new wired ethernet connection to no avail. When I try to connect to my router from firefox or epiphany I get a refused connection.

My connection type is DHCP (Automatic) as set under the Network Connections on Ubuntu.

My router is a D-Link WBR-2310

Power cycling my computer, router, and modem do nothing.

The led light on my ethernet port is lit, indicating the computer detected the cable.

These are the results of an ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:0c:6e:1e:c7:6e  
          inet6 addr: fe80::20c:6eff:fe1e:c76e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6624 (6.6 KB)
          Interrupt:23 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13408 (13.4 KB)  TX bytes:13408 (13.4 KB)

```

Please let me know if you need any more info, and properly explain any possible solutions so I don't mess them up, as I'm pretty new to all of this.

Oh, I also forgot to mention. A laptop running windows XP is able to connect with wireless to the router and the internet fine.

---

### Post by Nisstyre56 on 2009-06-25
Bump

Could someone give me some ideas? I have a feeling I'm missing something really simple with this.

---

### Post by jonobr on 2009-06-25
Hello

It appears you are not getting an ipaddress assigned from the router.

The ethernet connection is not aware of the router,
when it boots it says, here I am , can anyone tell me what my IP address should be.
The router would respond and say, here you go, here is your ip address and here is your other config information.

So, what you need to do is, encure your connection to the router (wired) is good.

Make sure your link light, showing it sees the network is on and (in most cases) green.
With that done,
i would try 

```
sudo dhclient
```

and see if you get an ip address.
Post the output back here.

If all that does not work, then go to a terminal and type

```
dmesg | grep eth0
```

post results again here

Thanks

---

### Post by Nisstyre56 on 2009-06-25
Here is the output of dhclient

```
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/pan0/fe:e4:cb:90:60:cd
Sending on   LPF/pan0/fe:e4:cb:90:60:cd
Listening on LPF/eth0/00:0c:6e:1e:c7:6e
Sending on   LPF/eth0/00:0c:6e:1e:c7:6e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

And dmesg | grep eth0

```

$ dmesg | grep eth0
[    2.682182] eth0: VIA Rhine II at 0xdc800000, 00:0c:6e:1e:c7:6e, IRQ 23.
[    2.682892] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 41e1.
[   25.643861] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   36.088008] eth0: no IPv6 routers present
```

I tested the ethernet cable on the other computer works fine. It is definitely showing a green light when connected to the Ubuntu box.

---

### Post by Nisstyre56 on 2009-06-25
So is there something amiss with my router's DHCP server?

Resetting it does nothing to help.

---

### Post by jonobr on 2009-06-25
Hello


The line 

> DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7

is showing a DHCP discover going to the network.

This is saying I want an ip address.

The 255.255.255.255 is ip addressing speak for "hey everyone"

So whats its trying to do is look for the address and nothing is responding.
Your router should respond to this with an ip address


Just to make sure its going out, 
could you post the result of

```
sudo tcpdump -vvvxNs0 -i eth0 host 255.255.255.255
```

Restart the dhclient and see what packets come out and if they are responded to

---

### Post by Nisstyre56 on 2009-06-25
All right, here you are.

```
$ sudo tcpdump -vvvxNs0 -i eth0 host 255.255.255.255
tcpdump: WARNING: eth0: no IPv4 address assigned
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
17:16:06.000662 IP (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328) 0.0.0.0.bootpc > 255.255.255.255.bootps: [udp sum ok] BOOTP/DHCP, Request from 00:0c:6e:1e:c7:6e (oui Unknown), length 300, xid 0xbb765b68, Flags [none] (0x0000)
	  Client-Ethernet-Address 00:0c:6e:1e:c7:6e (oui Unknown)
	  Vendor-rfc1048 Extensions
	    Magic Cookie 0x63825363
	    DHCP-Message Option 53, length 1: Discover
	    Hostname Option 12, length 3: "wes"
	    Parameter-Request Option 55, length 13: 
	      Subnet-Mask, BR, Time-Zone, Default-Gateway
	      Domain-Name, Domain-Name-Server, Option 119, Hostname
	      Netbios-Name-Server, Netbios-Scope, MTU, Classless-Static-Route
	      NTP
	    END Option 255, length 0
	    PAD Option 0, length 0, occurs 36
	0x0000:  4510 0148 0000 0000 8011 3996 0000 0000
	0x0010:  ffff ffff 0044 0043 0134 21c3 0101 0600
	0x0020:  bb76 5b68 0000 0000 0000 0000 0000 0000
	0x0030:  0000 0000 0000 0000 000c 6e1e c76e 0000
	0x0040:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0050:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0060:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0070:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0080:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0090:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00a0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00b0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00c0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00d0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00e0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00f0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0100:  0000 0000 0000 0000 6382 5363 3501 010c
	0x0110:  0377 6573 370d 011c 0203 0f06 770c 2c2f
	0x0120:  1a79 2aff 0000 0000 0000 0000 0000 0000
	0x0130:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0140:  0000 0000 0000 0000
17:16:11.002351 IP (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328) 0.0.0.0.bootpc > 255.255.255.255.bootps: [udp sum ok] BOOTP/DHCP, Request from 00:0c:6e:1e:c7:6e (oui Unknown), length 300, xid 0xbb765b68, secs 5, Flags [none] (0x0000)
	  Client-Ethernet-Address 00:0c:6e:1e:c7:6e (oui Unknown)
	  Vendor-rfc1048 Extensions
	    Magic Cookie 0x63825363
	    DHCP-Message Option 53, length 1: Discover
	    Hostname Option 12, length 3: "wes"
	    Parameter-Request Option 55, length 13: 
	      Subnet-Mask, BR, Time-Zone, Default-Gateway
	      Domain-Name, Domain-Name-Server, Option 119, Hostname
	      Netbios-Name-Server, Netbios-Scope, MTU, Classless-Static-Route
	      NTP
	    END Option 255, length 0
	    PAD Option 0, length 0, occurs 36
	0x0000:  4510 0148 0000 0000 8011 3996 0000 0000
	0x0010:  ffff ffff 0044 0043 0134 21be 0101 0600
	0x0020:  bb76 5b68 0005 0000 0000 0000 0000 0000
	0x0030:  0000 0000 0000 0000 000c 6e1e c76e 0000
	0x0040:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0050:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0060:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0070:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0080:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0090:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00a0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00b0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00c0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00d0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00e0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00f0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0100:  0000 0000 0000 0000 6382 5363 3501 010c
	0x0110:  0377 6573 370d 011c 0203 0f06 770c 2c2f
	0x0120:  1a79 2aff 0000 0000 0000 0000 0000 0000
	0x0130:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0140:  0000 0000 0000 0000
17:16:24.001128 IP (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328) 0.0.0.0.bootpc > 255.255.255.255.bootps: [udp sum ok] BOOTP/DHCP, Request from 00:0c:6e:1e:c7:6e (oui Unknown), length 300, xid 0xbb765b68, secs 18, Flags [none] (0x0000)
	  Client-Ethernet-Address 00:0c:6e:1e:c7:6e (oui Unknown)
	  Vendor-rfc1048 Extensions
	    Magic Cookie 0x63825363
	    DHCP-Message Option 53, length 1: Discover
	    Hostname Option 12, length 3: "wes"
	    Parameter-Request Option 55, length 13: 
	      Subnet-Mask, BR, Time-Zone, Default-Gateway
	      Domain-Name, Domain-Name-Server, Option 119, Hostname
	      Netbios-Name-Server, Netbios-Scope, MTU, Classless-Static-Route
	      NTP
	    END Option 255, length 0
	    PAD Option 0, length 0, occurs 36
	0x0000:  4510 0148 0000 0000 8011 3996 0000 0000
	0x0010:  ffff ffff 0044 0043 0134 21b1 0101 0600
	0x0020:  bb76 5b68 0012 0000 0000 0000 0000 0000
	0x0030:  0000 0000 0000 0000 000c 6e1e c76e 0000
	0x0040:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0050:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0060:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0070:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0080:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0090:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00a0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00b0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00c0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00d0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00e0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00f0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0100:  0000 0000 0000 0000 6382 5363 3501 010c
	0x0110:  0377 6573 370d 011c 0203 0f06 770c 2c2f
	0x0120:  1a79 2aff 0000 0000 0000 0000 0000 0000
	0x0130:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0140:  0000 0000 0000 0000
17:16:39.002125 IP (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328) 0.0.0.0.bootpc > 255.255.255.255.bootps: [udp sum ok] BOOTP/DHCP, Request from 00:0c:6e:1e:c7:6e (oui Unknown), length 300, xid 0xbb765b68, secs 33, Flags [none] (0x0000)
	  Client-Ethernet-Address 00:0c:6e:1e:c7:6e (oui Unknown)
	  Vendor-rfc1048 Extensions
	    Magic Cookie 0x63825363
	    DHCP-Message Option 53, length 1: Discover
	    Hostname Option 12, length 3: "wes"
	    Parameter-Request Option 55, length 13: 
	      Subnet-Mask, BR, Time-Zone, Default-Gateway
	      Domain-Name, Domain-Name-Server, Option 119, Hostname
	      Netbios-Name-Server, Netbios-Scope, MTU, Classless-Static-Route
	      NTP
	    END Option 255, length 0
	    PAD Option 0, length 0, occurs 36
	0x0000:  4510 0148 0000 0000 8011 3996 0000 0000
	0x0010:  ffff ffff 0044 0043 0134 21a2 0101 0600
	0x0020:  bb76 5b68 0021 0000 0000 0000 0000 0000
	0x0030:  0000 0000 0000 0000 000c 6e1e c76e 0000
	0x0040:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0050:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0060:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0070:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0080:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0090:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00a0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00b0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00c0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00d0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00e0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00f0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0100:  0000 0000 0000 0000 6382 5363 3501 010c
	0x0110:  0377 6573 370d 011c 0203 0f06 770c 2c2f
	0x0120:  1a79 2aff 0000 0000 0000 0000 0000 0000
	0x0130:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0140:  0000 0000 0000 0000
17:16:51.002133 IP (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328) 0.0.0.0.bootpc > 255.255.255.255.bootps: [udp sum ok] BOOTP/DHCP, Request from 00:0c:6e:1e:c7:6e (oui Unknown), length 300, xid 0xbb765b68, secs 45, Flags [none] (0x0000)
	  Client-Ethernet-Address 00:0c:6e:1e:c7:6e (oui Unknown)
	  Vendor-rfc1048 Extensions
	    Magic Cookie 0x63825363
	    DHCP-Message Option 53, length 1: Discover
	    Hostname Option 12, length 3: "wes"
	    Parameter-Request Option 55, length 13: 
	      Subnet-Mask, BR, Time-Zone, Default-Gateway
	      Domain-Name, Domain-Name-Server, Option 119, Hostname
	      Netbios-Name-Server, Netbios-Scope, MTU, Classless-Static-Route
	      NTP
	    END Option 255, length 0
	    PAD Option 0, length 0, occurs 36
	0x0000:  4510 0148 0000 0000 8011 3996 0000 0000
	0x0010:  ffff ffff 0044 0043 0134 2196 0101 0600
	0x0020:  bb76 5b68 002d 0000 0000 0000 0000 0000
	0x0030:  0000 0000 0000 0000 000c 6e1e c76e 0000
	0x0040:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0050:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0060:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0070:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0080:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0090:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00a0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00b0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00c0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00d0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00e0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00f0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0100:  0000 0000 0000 0000 6382 5363 3501 010c
	0x0110:  0377 6573 370d 011c 0203 0f06 770c 2c2f
	0x0120:  1a79 2aff 0000 0000 0000 0000 0000 0000
	0x0130:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0140:  0000 0000 0000 0000
17:16:58.007129 IP (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328) 0.0.0.0.bootpc > 255.255.255.255.bootps: [udp sum ok] BOOTP/DHCP, Request from 00:0c:6e:1e:c7:6e (oui Unknown), length 300, xid 0xbb765b68, secs 52, Flags [none] (0x0000)
	  Client-Ethernet-Address 00:0c:6e:1e:c7:6e (oui Unknown)
	  Vendor-rfc1048 Extensions
	    Magic Cookie 0x63825363
	    DHCP-Message Option 53, length 1: Discover
	    Hostname Option 12, length 3: "wes"
	    Parameter-Request Option 55, length 13: 
	      Subnet-Mask, BR, Time-Zone, Default-Gateway
	      Domain-Name, Domain-Name-Server, Option 119, Hostname
	      Netbios-Name-Server, Netbios-Scope, MTU, Classless-Static-Route
	      NTP
	    END Option 255, length 0
	    PAD Option 0, length 0, occurs 36
	0x0000:  4510 0148 0000 0000 8011 3996 0000 0000
	0x0010:  ffff ffff 0044 0043 0134 218f 0101 0600
	0x0020:  bb76 5b68 0034 0000 0000 0000 0000 0000
	0x0030:  0000 0000 0000 0000 000c 6e1e c76e 0000
	0x0040:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0050:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0060:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0070:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0080:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0090:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00a0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00b0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00c0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00d0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00e0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00f0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0100:  0000 0000 0000 0000 6382 5363 3501 010c
	0x0110:  0377 6573 370d 011c 0203 0f06 770c 2c2f
	0x0120:  1a79 2aff 0000 0000 0000 0000 0000 0000
	0x0130:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0140:  0000 0000 0000 0000
17:17:05.001280 IP (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328) 0.0.0.0.bootpc > 255.255.255.255.bootps: [udp sum ok] BOOTP/DHCP, Request from 00:0c:6e:1e:c7:6e (oui Unknown), length 300, xid 0xbb765b68, secs 59, Flags [none] (0x0000)
	  Client-Ethernet-Address 00:0c:6e:1e:c7:6e (oui Unknown)
	  Vendor-rfc1048 Extensions
	    Magic Cookie 0x63825363
	    DHCP-Message Option 53, length 1: Discover
	    Hostname Option 12, length 3: "wes"
	    Parameter-Request Option 55, length 13: 
	      Subnet-Mask, BR, Time-Zone, Default-Gateway
	      Domain-Name, Domain-Name-Server, Option 119, Hostname
	      Netbios-Name-Server, Netbios-Scope, MTU, Classless-Static-Route
	      NTP
	    END Option 255, length 0
	    PAD Option 0, length 0, occurs 36
	0x0000:  4510 0148 0000 0000 8011 3996 0000 0000
	0x0010:  ffff ffff 0044 0043 0134 2188 0101 0600
	0x0020:  bb76 5b68 003b 0000 0000 0000 0000 0000
	0x0030:  0000 0000 0000 0000 000c 6e1e c76e 0000
	0x0040:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0050:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0060:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0070:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0080:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0090:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00a0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00b0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00c0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00d0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00e0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x00f0:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0100:  0000 0000 0000 0000 6382 5363 3501 010c
	0x0110:  0377 6573 370d 011c 0203 0f06 770c 2c2f
	0x0120:  1a79 2aff 0000 0000 0000 0000 0000 0000
	0x0130:  0000 0000 0000 0000 0000 0000 0000 0000
	0x0140:  0000 0000 0000 0000



```

---

### Post by Nisstyre56 on 2009-06-25
By the way, booting up with the Ubuntu Live cd, it doesn't work on there either.

Nor does it work when connected directly to the modem/internet.

---

### Post by Nisstyre56 on 2009-06-25
I'd really appreciate if soeone could help me fix this...

---

### Post by Nisstyre56 on 2009-06-26
So I just completely reinstalled Ubuntu and now the light on my ethernet port is not even on.

I have tried the following:

[http://ubuntuforums.org/showpost.php?p=7276275&postcount=8](http://ubuntuforums.org/showpost.php?p=7276275&postcount=8)

[http://ubuntuforums.org/showpost.php?p=5997728&postcount=11](http://ubuntuforums.org/showpost.php?p=5997728&postcount=11)

The second one, changing it to half duplex and 10mp/sec caused the network icon to change and attempt to connect, but ultimately fail.

This is strange, it worked fine a week ago when I installed Ubuntu the first time.

---

### Post by Iowan on 2009-06-26
[Here]("http://ubuntuforums.org/showthread.php?t=1156441") is another thing to try.

---

