---
title: "DHCP client problems"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by sheirys on 2011-03-28
Hi everyone i`m new on ubuntu. :popcorn:

my dhclient cant get DHCPOFFER.

```

# dhclient3 -d eth0
There is already a pid file /var/run/dhclient.pid with pid 1645
removed stale PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:18:84:a0:d7:41
Sending on   LPF/eth0/00:18:84:a0:d7:41
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

on windows 7 everything works fine.
here is ipconfig /all on windows

```

Windows IP Configuration

   Host Name . . . . . . . . . . . . : Tomas-PC
   Primary Dns Suffix  . . . . . . . : 
   Node Type . . . . . . . . . . . . : Broadcast
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : bxlan.su.lt

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : bxlan.su.lt
   Description . . . . . . . . . . . : Realtek RTL8102E/RTL8103E Family PCI-E Fast Ethernet NIC (NDIS 6.20)
   Physical Address. . . . . . . . . : 00-18-84-A0-D7-41
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 192.168.5.29(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.252.0
   Lease Obtained. . . . . . . . . . : 2011 m. kovo 27 d. 20:26:40
   Lease Expires . . . . . . . . . . : 2011 m. kovo 28 d. 08:26:40
   Default Gateway . . . . . . . . . : 192.168.4.1
   DHCP Server . . . . . . . . . . . : 192.168.4.1
   DNS Servers . . . . . . . . . . . : 192.168.4.1
   NetBIOS over Tcpip. . . . . . . . : Enabled

```

Also i had archlinux. in archlinux dhcpcd worked fine with 'dhcpcd -J eth0' option. Here is 'man dhcpcd' about -J option in archlinux:
```

-J   Instructs the DHCP server to broadcast replies back to the client.
     Normally this is only set for non Ethernet interfaces,
     such as FireWire and InfiniBand.
     In most instances, will set this automatically.

```

So, how i should configure my dhclient that it work like archlinux 'dhcpcd -J' ?

---

