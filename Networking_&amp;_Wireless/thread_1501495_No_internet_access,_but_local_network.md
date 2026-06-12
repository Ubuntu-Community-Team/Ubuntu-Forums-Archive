---
title: "No internet access, but local network"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by Nikhil Chelliah on 2010-06-04
My computer seems to have developed the same problem over the last 24 hours.  I'm running Kubuntu 10.04; I dual-boot with Windows and its internet connection is fine.

I ran the commands that you guys recommended and saved the output, but I'm not sure where to go next.

```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:22:15:04:3a:af  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1b:21:19:e1:16  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12300 (12.3 KB)  TX bytes:12300 (12.3 KB)
```

```
$ ping 4.2.2.1
connect: Network is unreachable
```

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

Thanks for the help so far.

---

### Post by dineshs on 2010-06-04
Are you using both ethernet ports?
Or only one to which the modem is connected?
Is it a DSL modem?
Who is the service provider?

---

### Post by Nikhil Chelliah on 2010-06-04
I'm only using one port (Intel PCI card), but because you've reminded me, I'll shut down the computer and try the other port (Asus P5Q motherboard).

The cord does run to a router connected to a DSL modem.  The ISP is Embarq.

**Edit:** Switching ethernet ports didn't help.  Still works in Windows but not in Linux.

---

### Post by dineshs on 2010-06-04
Can you post the result of```
 ipconfig /all
``` while in[COLOR="Red"] windows[/COLOR]

---

### Post by Nikhil Chelliah on 2010-06-04
Here it is:

```
> ipconfig /all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : nikhil-desktop
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection 2:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller(NDIS6.20)
   Physical Address. . . . . . . . . : 00-22-15-04-3A-AF
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Intel(R) PRO/1000 GT Desktop Adapter
   Physical Address. . . . . . . . . : 00-1B-21-19-E1-16
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::39b5:27e7:278:1cb8%11(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.1.100(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Friday, June 04, 2010 5:02:25 AM
   Lease Expires . . . . . . . . . . : Saturday, June 05, 2010 5:02:25 AM
   Default Gateway . . . . . . . . . : 192.168.1.1
   DHCP Server . . . . . . . . . . . : 192.168.1.1
   DHCPv6 IAID . . . . . . . . . . . : 234887969
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-12-4B-52-E7-00-1B-21-19-E1-16

   DNS Servers . . . . . . . . . . . : 208.33.159.39
                                       63.162.197.99
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter isatap.{07E18253-F6DE-41CB-B7E8-58DC6758B3F2}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter 6TO4 Adapter:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 11:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e74:343e:e9ea:b8ff:aea3(Preferred)
   Link-local IPv6 Address . . . . . : fe80::343e:e9ea:b8ff:aea3%14(Preferred)
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter isatap.{4DD2E50A-69D6-4398-BA85-1F2FF8C71165}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
```

---

### Post by dineshs on 2010-06-04
Is your LAN enabled?Can you run
```
sudo ifconfig eth0 up
```
```
sudo ifconfig eth1 up
```
```
sudo dhclient
```
and then post the output of```
ifconfig -a
```

---

### Post by Nikhil Chelliah on 2010-06-04
That solved the problem.  Do you have any idea if this will be a recurring problem?

Regardless, thanks for all the help, Dinesh!  I hope this helps the original poster so that the issue can be marked as solved.

---

### Post by dineshs on 2010-06-04
> Do you have any idea if this will be a recurring problem?
I dont think so.Anyway happy to hear your problem is solved

---

### Post by Iowan on 2010-06-04
Posts separated into new thread from [here]("http://ubuntuforums.org/showthread.php?t=1495953"). Marked it as [SOLVED].

---

