---
title: "Howto Setup broadband connection that DOESNT require username and password"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by sabelo on 2011-01-11
Hi, im using Ubuntu 9.04...How do i setup a broadband connection that DOES NOT require a username and password i tried pppoeconf but it wont let me proceed without entering something in the username and password fields. on XP i jus plug in my ethernet cable and it works but it doest on ubuntu... please help.

---

### Post by aromo on 2011-01-11
> **sabelo said:**
> Hi, im using Ubuntu 9.04...How do i setup a broadband connection that DOES NOT require a username and password i tried pppoeconf but it wont let me proceed without entering something in the username and password fields. on XP i jus plug in my ethernet cable and it works but it doest on ubuntu... please help.

It should, you just have to make sure your NIC is in the same submet as your gateway (ifconfig) and add any static route (route).  That is true if you are setting up static IP addresses.  If your gateway is also a DHCP server, it should work as it does in XP.  Try pinging the address of your gateway and post the output, also post the output of ifconfig.

---

### Post by sabelo on 2011-04-25
Hi i am now experiencing the same problem in ubuntu 10.10, how do i go about doing what you explained here above.

---

### Post by mick222 on 2011-04-25
try right clicking the network icon add new connection make sure that that automatic dhcp is selected on the ipv4 settings.
 Are you sure it has no security as it might require the wap code to be entered.

---

### Post by dineshs on 2011-04-25
Please post the results of ```
ipconfig /all
``` from [COLOR="Red"]windows[/COLOR] and ```
sudo lshw -C network
route -n
```from [COLOR="Red"]ubuntu[/COLOR]

---

### Post by sabelo on 2011-04-26
hi, the results are like this:
sabelo@Little-Guitarista:~$ sudo lshw -C network
[sudo] password for sabelo: 
  *-network                             
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: c4:17:fe:e0:8f:1c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f8900000-f890ffff
  *-network DISABLED
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 01
       serial: c8:0a:a9:6a:81:1f
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 firmware=sb v2.07 latency=0 link=yes multicast=yes port=MII
       resources: irq:16 memory:f8a00000-f8a0ffff
sabelo@Little-Guitarista:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: c4:17:fe:e0:8f:1c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f8900000-f890ffff
  *-network DISABLED
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 01
       serial: c8:0a:a9:6a:81:1f
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 firmware=sb v2.07 latency=0 link=yes multicast=yes port=MII
       resources: irq:16 memory:f8a00000-f8a0ffff
sabelo@Little-Guitarista:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
sabelo@Little-Guitarista:~$ 

and for ipconfig i get this result :

Microsoft Windows [Version 6.1.7600]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Users\Sabelo>ipconfig /all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : Lil-Guitarista
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : Home

Wireless LAN adapter Wireless Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : openhotspot.net
   Description . . . . . . . . . . . : Atheros AR9285 Wireless Network Adapter
   Physical Address. . . . . . . . . : C4-17-FE-E0-8F-1C
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : Home
   Description . . . . . . . . . . . : Broadcom NetLink (TM) Gigabit Ethernet
   Physical Address. . . . . . . . . : C8-0A-A9-6A-81-1F
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::b4e3:f7ec:6a85:3175%13(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.1.9(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : 26 April 2011 04:03:43 PM
   Lease Expires . . . . . . . . . . : 27 April 2011 04:03:43 PM
   Default Gateway . . . . . . . . . : 192.168.1.1
   DHCP Server . . . . . . . . . . . : 192.168.1.1
   DHCPv6 IAID . . . . . . . . . . . : 298322601
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-13-75-9D-B0-C8-0A-A9-6A-81-1F

   DNS Servers . . . . . . . . . . . : 192.168.1.1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter Bluetooth Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Bluetooth Device (Personal Area Network)
   Physical Address. . . . . . . . . : F0-7B-CB-C1-48-D1
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{28EDC29F-C563-43EF-901D-C59BB7A920F8}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.Home:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : Home
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 14:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.openhotspot.net:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #3
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e76:30f9:29b4:d628:682d(Pref
erred)
   Link-local IPv6 Address . . . . . : fe80::30f9:29b4:d628:682d%19(Preferred)
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled

C:\Users\Sabelo>

---

### Post by sabelo on 2011-04-26
i have it on automatic DHCP, in the ipv4 settings but still nothing, and the network manager icon comes and goes as it pleases on the panel..but i went to system preferences and networking to get it  from there.

---

### Post by dineshs on 2011-04-26
It seems your ethernet is disabled.Can you post the output of
```
cat /etc/network/interfaces
cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by sabelo on 2011-04-26
hi, the output is as follows:

sabelo@Little-Guitarista:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual
sabelo@Little-Guitarista:~$ 

and 

sabelo@Little-Guitarista:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
sabelo@Little-Guitarista:~$

---

### Post by dineshs on 2011-04-26
please run```
sudo gedit /etc/network/interfaces
```
The file so opened should have only the following lines (delete all other lines) ```
auto lo
iface lo inet loopback
```
Save and restart PC
Rightclick Network manager icon on right top of the panel and ensure that enable networking is ticked.Now see if the connection is working.If not run ```
sudo dhclient eth0
```and try again (please post result of sudo dhclient eth0 )

---

### Post by sabelo on 2011-04-26
Thank you very much :) :) that worked, im now connected and the network manager icon showed up again...:) thank you sooo much :)

---

### Post by dineshs on 2011-04-26
Happy to hear that.Please mark the thread as solved via thread tools

---

### Post by sabelo on 2011-04-26
thank you very much :) :), that worked and my connection is fine now. thank you sooo much :)  i really apreciate it. :)

---

### Post by sabelo on 2011-04-26
will do that...

---

