---
title: "What is pan0? &amp; Why 4 nameservers?"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by Bruce M. on 2008-12-29
Hi Folks,

**[COLOR="Blue"]Please note:[/COLOR]** I'm running Xubuntu 8.10-64bit

Two questiions:

1. What is this **pan0** I see?
```
bruloo@bruloo:~$ sudo dhclient
[sudo] password for bruloo: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/pan0/56:e0:82:53:6a:2b
Sending on   LPF/pan0/56:e0:82:53:6a:2b
Listening on LPF/eth0/00:13:d3:c3:c4:b7
Sending on   LPF/eth0/00:13:d3:c3:c4:b7
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 201.235.217.15 from 201.235.217.1
DHCPREQUEST of 201.235.217.15 on eth0 to 255.255.255.255 port 67
DHCPACK of 201.235.217.15 from 201.235.217.1
bound to 201.235.217.15 -- renewal in 8993 seconds.

bruloo@bruloo:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:d3:c3:c4:b7  
          inet addr:201.235.217.15  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:10445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6147 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4026830 (4.0 MB)  TX bytes:652871 (652.8 KB)
          Interrupt:21 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7972 (7.9 KB)  TX bytes:7972 (7.9 KB)

pan0      Link encap:Ethernet  HWaddr 56:e0:82:53:6a:2b  
          inet6 addr: fe80::54e0:82ff:fe53:6a2b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:2988 (2.9 KB)

bruloo@bruloo:~$ 
```

**[CENTER]---------------[/CENTER]**
**[SIZE="6"][CENTER]EDIT[/CENTER][/SIZE]**

OK, I found out here: [Why is pan0 showing up in Firestarter?]("http://ubuntuforums.org/showthread.php?t=957909") that it is *Personal Area Networking Profile (PAN)* and since I use *nothing* bluetooth, I did as the OP did and deleted everything bluetooth from my system except *libbluetooth3* as the OP said:
> because it looked like it would have removed a bunch of other applications if I had uninstalled it.
**[CENTER]---------------[/CENTER]**

*[CENTER]So that only leaves me with the second question:[/CENTER]*

and second: Why does my **resolv.conf** have 4 nameservers?
```
bruloo@bruloo:~$ cat /etc/resolv.conf
nameserver 200.49.130.20
nameserver 200.49.130.21
nameserver 200.49.130.32
nameserver 172.20.2.12

bruloo@bruloo:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet dhcp
bruloo@bruloo:~$ 

```

If I edit my **resolv.conf** to include only the top three, on next reboot it has the four again.

Thanks
Bruce

---

### Post by Bruce M. on 2008-12-30
bump---

Q #2

---

### Post by bobpaul on 2009-03-02
> **Bruce M. said:**
> 

and second: Why does my **resolv.conf** have 4 nameservers?

If I edit my **resolv.conf** to include only the top three, on next reboot it has the four again.

Which name server shouldn't be there?

Resolve.conf is edited by NetworkManager every time you connect to a network. This should reflect the name servers that were acquired from DHCP. Are you sure your DHCP server isn't supplying all 4? Try editing reslov.conf to make it as you want and then run "sudo dhclient". Did your resolv.conf return to the way you didn't like? If so, fix your DHCP server configuration.

---

### Post by Bruce M. on 2009-03-03
> **bobpaul said:**
> Which name server shouldn't be there?

Resolve.conf is edited by NetworkManager every time you connect to a network. This should reflect the name servers that were acquired from DHCP. Are you sure your DHCP server isn't supplying all 4? Try editing reslov.conf to make it as you want and then run "sudo dhclient". Did your resolv.conf return to the way you didn't like? If so, fix your DHCP server configuration.

Well, at the time, I was using Network Manager and editing the file and putting in three didn't help. It is overwritten by NM, and googling for help I found that resolve.config (even today) only reads 3 entries.

So the fourth entry is never read or used. and since it starts with a 172 I don't worry about it.

Also, the problem is with my ISP, not my machine, the techies have been "living here" for months trying to figure out why I'm getting micro-cuts every 10 minutes or so starting at +/- noon.

Today I use Wicd to manage my networking. Much better.

---

