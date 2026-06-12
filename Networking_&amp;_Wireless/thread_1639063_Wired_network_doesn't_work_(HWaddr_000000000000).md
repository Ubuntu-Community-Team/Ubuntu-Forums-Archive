---
title: "Wired network doesn't work (HWaddr 00:00:00:00:00:00)"
date: 2010-12-06
forum: Networking &amp; Wireless
---

### Post by peterdm on 2010-12-06
My desktop PC has 2 NICs. I have Ubuntu on it since several years, and I remember that both eth0 and eth1 used to work. However, I discovered recently that currently only eth0 works, and eth1 is dead, but I don't know why. It's been a while since I've tried eth1, so I have no idea when exactly it broke. I suspect the problem may be related to the fact that the MAC address is incorrect: it is set to 00:00:00:00:00:00, which seems wrong. But I have no idea how this happened...

Any idea what might be wrong and how I can fix it? Here is some output which I think is useful:

```

peter@cheetah:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:18:f3:68:42:78  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe68:4278/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52966 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39842 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50305900 (50.3 MB)  TX bytes:6654424 (6.6 MB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10860 (10.8 KB)  TX bytes:10860 (10.8 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```

peter@cheetah:~$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 00
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:fe8fc000-fe8fffff ioport:a800(size=256) memory:fe8c0000-fe8dffff
  *-network
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 4
       bus info: pci@0000:05:04.0
       logical name: eth0
       version: 14
       serial: 00:18:f3:68:42:78
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=192.168.0.100 latency=64 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:19 memory:feaf4000-feaf7fff ioport:c800(size=256) memory:feac0000-feadffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

---

### Post by pricetech on 2010-12-06
Your disabled NIC is your ETH1 obviously.  Disabled in BIOS maybe ???  Otherwise I'd be looking at replacing it.

---

### Post by peterdm on 2010-12-07
I guess a broken NIC is possible, however unlikely... I'll check my bios settings anyway. Another reason why I think the problem is software related rather than hardware related is that ifconfig is giving me different NIC settings every time. Today I seem to have *eth0* disabled and *eth1-eth0*... Physically, today's eth1-eth0 is yesterday's eth0. I guess the kernel decides on the names somehow, but I can't understand why it is different every time I reboot???

```

peter@cheetah:~$ sudo lshw -C network
[sudo] password for peter: 
  *-network DISABLED      
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:fe8fc000-fe8fffff ioport:a800(size=256) memory:fe8c0000-fe8dffff
  *-network
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 4
       bus info: pci@0000:05:04.0
       logical name: eth1-eth0
       version: 14
       serial: 00:18:f3:68:42:78
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=192.168.0.100 latency=64 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=1GB/s
       resources: irq:19 memory:feaf4000-feaf7fff ioport:c800(size=256) memory:feac0000-feadffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

```

peter@cheetah:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1-eth0 Link encap:Ethernet  HWaddr 00:18:f3:68:42:78  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe68:4278/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2796 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2440 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2079247 (2.0 MB)  TX bytes:409032 (409.0 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9964 (9.9 KB)  TX bytes:9964 (9.9 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by peterdm on 2010-12-07
[LIST]
[*]The NIC is definitely enabled in the BIOS, I checked to confirm.
[*]The NIC is definitely not broken: it works in Windows 7. Note even in Windows the MAC address was still set to 00:00:00:00:00:00, but that didn't seem to have any ill effects in Windows.
[/LIST]

So the question then is:
[LIST]
[*]Is it possibly a driver problem in Linux? I've read some bad reports about the sky2 driver (this is the driver that is being used) dating a couple of years back. Since I did not find any recent reports, I presume that these problems have meanwhile been fixed (admittedly, that may be a dangerous assumption).
[*]What could possibly have happened over the last couple of years to cause the NIC to "forget" its own MAC address? I never consciously "updated" the firmware or anything, but since it's an onboard NIC, who knows what the BIOS might have done to it... Actually I have no idea, just thinking out loud here.
[/LIST]

Ideas welcome...

```

C:\Users\Peter>ipconfig /all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : Cheetah
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : telenet.be

Ethernet adapter Local Area Connection 3:

   Connection-specific DNS Suffix  . : telenet.be
   Description . . . . . . . . . . . : Generic Marvell Yukon 88E8055 PCI-E Gigab
it Ethernet Controller
   Physical Address. . . . . . . . . : 00-00-00-00-00-00
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::d9e8:6529:da4d:ed49%16(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.0.198(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : dinsdag 7 december 2010 17:50:46
   Lease Expires . . . . . . . . . . : woensdag 8 december 2010 17:50:46
   Default Gateway . . . . . . . . . : 192.168.0.1
   DHCP Server . . . . . . . . . . . : 192.168.0.1
   DHCPv6 IAID . . . . . . . . . . . : 352321536
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-14-26-EC-0C-00-18-F3-68-80-98

   DNS Servers . . . . . . . . . . . : 192.168.0.1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter Local Area Connection 2:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : telenet.be
   Description . . . . . . . . . . . : Marvell Yukon 88E8001/8003/8010 PCI Gigab
it Ethernet Controller
   Physical Address. . . . . . . . . : 00-18-F3-68-42-78
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.telenet.be:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : telenet.be
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 12:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:5ef5:79fd:4ca:2e1:a11e:9242(Prefer
red)
   Link-local IPv6 Address . . . . . : fe80::4ca:2e1:a11e:9242%15(Preferred)
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled

```

---

### Post by pricetech on 2010-12-07
> **peterdm said:**
>  Note even in Windows the MAC address was still set to 00:00:00:00:00:00 

Ran into similar some years ago.  It seems that, for whatever reason, the MAC is not "burned in" any more.  You have to set it in the BIOS or with some utility furnished by the MoBo manufacturer.

Check the area of the motherboard around the onboard NIC and see if you see a MAC address.  That would be the one that belongs to that NIC.  See if you can enter it in BIOS somewhere.  If not, check the manufacturer's website.

Agreed you have some bizarre behaviour going on.  Outside of assigning a proper MAC address, I may not be much help.

Do that and let's see what happens.

---

### Post by uncaspi on 2010-12-07
Hi sorry to interrupt, but have you tried to set the hw from the ifconfig command? sudo ifconfig eth1 hw ether 00:04:fe:10:20:30

---

### Post by peterdm on 2010-12-17
Setting the hw from the command line works, but it just "spoofs" the mac address. It's not a persistent solution. I'll try looking for a BIOS utility to set the mac address back.

---

### Post by MadSpirit on 2010-12-18
Hello!
 
I have same problem with my Marvell Yukon 88E8055 adapter, still cannot find any solution. :/
 
Microsoft Windows [Version 6.1.7600]
Copyright (c) 2009 Microsoft Corporation. All rights reserved.
C:\Users\MadSpirit>ipconfig /all
 
Windows IP Configuration
Host Name . . . . . . . . . . . . : MadSpirit-PC
Primary Dns Suffix . . . . . . . :
Node Type . . . . . . . . . . . . : Hybrid
IP Routing Enabled. . . . . . . . : No
WINS Proxy Enabled. . . . . . . . : No
DNS Suffix Search List. . . . . . : lan
 
Ethernet adapter LAN2:
 
Connection-specific DNS Suffix . : lan
Description . . . . . . . . . . . : Generic Marvell Yukon 88E8055 PCI-E Gigab
it Ethernet Controller
Physical Address. . . . . . . . . : 00-00-00-00-00-00
DHCP Enabled. . . . . . . . . . . : Yes
Autoconfiguration Enabled . . . . : Yes
Link-local IPv6 Address . . . . . : fe80::9e1:2781:c26a:5ac2%14(Preferred)
IPv4 Address. . . . . . . . . . . : 192.168.1.64(Preferred)
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Lease Obtained. . . . . . . . . . : 18. detsember 2010. a. 23:42:42
Lease Expires . . . . . . . . . . : 20. detsember 2010. a. 0:00:23
Default Gateway . . . . . . . . . : 192.168.1.254
DHCP Server . . . . . . . . . . . : 192.168.1.254
DHCPv6 IAID . . . . . . . . . . . : 301989888
DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-12-40-0D-CF-00-18-F3-32-C2-5F
DNS Servers . . . . . . . . . . . : 192.168.1.254
NetBIOS over Tcpip. . . . . . . . : Enabled
 
Tunnel adapter Local Area Connection* 12:
 
Connection-specific DNS Suffix . :
Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
DHCP Enabled. . . . . . . . . . . : No
Autoconfiguration Enabled . . . . : Yes
IPv6 Address. . . . . . . . . . . : 2001:0:5ef5:79fd:2456:11c0:3f57:febf(Pref
erred)
Link-local IPv6 Address . . . . . : fe80::2456:11c0:3f57:febf%10(Preferred)
Default Gateway . . . . . . . . . : ::
NetBIOS over Tcpip. . . . . . . . : Disabled

---

### Post by musikmann on 2011-01-12
Having the same issue on Fedora...  Did you figure anything out?

Add this to the end of /etc/rc.local Its a hack for now:
```
...
ifconfig eth0 hw ether 00:04:fe:11:22:33
service NetworkManager restart
```

---

### Post by tkoopa on 2011-08-27
Thanks musikmann, your solution worked with my similar problem [http://ubuntuforums.org/showthread.php?t=1834124](http://ubuntuforums.org/showthread.php?t=1834124)

---

