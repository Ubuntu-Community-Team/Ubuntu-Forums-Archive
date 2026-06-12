---
title: "Ubuntu 9.10 can't get any connection!"
date: 2010-04-24
forum: Networking &amp; Wireless
---

### Post by Cartoonman on 2010-04-24
I'm pretty new to Ubuntu, and i'm not sure exactly what happened, but after i installed Kubuntu desktop via package manager, when i switched interfaces, i suddenly had no connection to the internet whatsoever. i get connection from the auto-DHCP server. my router in turn has it's own local DHCP server that applies static IP's to the computers in my network. i'm a main Windows user, but i do have good experience with Unix on my mac. 

I have Ubuntu installed on a USB on a W-XP system, but it works fine, aside from the start mess where it complains about bad superblocks in dev/sr1, but it loads fine anyway, though i wish to understand (and fix) that issue in the future.

I looked all over google for a solution, but i couldn't see much. i'm posting from my XP, so that shows that the Ethernet cable and router, a Linksys, is working fine. i tried 2 time on Ubuntu, but still no internet. i couldn't even get into my router settings, so i figured theres something i messed up apparently in Ubuntu.

i did those Terminal cmd-line checks, but one thing stood out from the other checks, where i put in 
```
route -n
```

and all i got was:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use  Iface
```

nothing underneath, even with manual settings. though when i put in the settings via terminal, it kept complaining that the subnet mask (set to 255.255.255.0) didn't match with the host IP. i checked my settings on my router on my other computer, and it said it was indeed 255.255.255.0. I'm guessing that for some reason, Ubuntu doesn't see the router, even though it sees my Network Card. 

I ran a system test on my network, but all it told me was the obvious; i have no internet. i'm stumped on what i can do without killing Ubuntu in the process. Got ideas?:confused:

---

### Post by Iowan on 2010-04-24
**ifconfig -a** will probably show no IP address - no surprise...
You might try > dhclient eth0

---

### Post by Cartoonman on 2010-04-25
thanks for the reply. i did it, and it worked?

lets just say, ubuntu is telling me i'm disconnected, while i'm currently posting on Ubuntu Forums using Ubuntu.

the Dhcp client spit this out:

```
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:16:76:1e:23:9f
Sending on   LPF/eth0/00:16:76:1e:23:9f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.101 from 192.168.1.1
DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.101 from 192.168.1.1
bound to 192.168.1.101 -- renewal in 81910 seconds.

```and oddly enough, ubuntu thinks i'm still disconnected, but i can now ping, and i can now access the web. however, when i go to the network icon above in Gnome, and i try to connect using eth0, i suddenly use internet totally, till i dhClient terminal. odd. 

i'll include ifconfig for both on and off internet.


ON:
```
eth0      Link encap:Ethernet  HWaddr 00:16:76:1e:23:9f  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:fe1e:239f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2226 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1958504 (1.9 MB)  TX bytes:381553 (381.5 KB)
          Interrupt:21 Base address:0xde00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```OFF:
```
eth0      Link encap:Ethernet  HWaddr 00:16:76:1e:23:9f  
          inet6 addr: fe80::216:76ff:fe1e:239f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2371 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2277 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2064754 (2.0 MB)  TX bytes:399697 (399.6 KB)
          Interrupt:21 Base address:0xde00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

the only difference i can see is the absence of an IP address on the second one. I have no idea what is going on. if i try to get eth0 working via network connections, i end up without network. dhclient seems to work as long as i don't touch anything else.

---

### Post by Iowan on 2010-04-26
The "dhclient" trick bypasses Network Manager (which gets all huffy as a result :)). You can see if [this]("http://ubuntuforums.org/showpost.php?p=9166366&postcount=2") helps.

---

### Post by Cartoonman on 2010-04-29
hmm, it seemed that the first one, the config for NM was set to False, although even after i changed it to true, it couldn't connect. So, i tried to get rid of eth0 connection, and make a new wired connection. strangely enough, it was able to connect by itself. i guess the config for Eth0 was somehow corrupted i guess. idk. maybe it was the config that was set to false. 

anyways, thanks for helping me! i'm finally back online on Ubuntu.:)

---

### Post by Iowan on 2010-04-29
Hope it STAYS fixed... :)
_IF_ it does...
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by tw11 on 2010-04-29
hey, i had a similar problem and typing dhclient eth0 solved the problem. i'm wondering how do you delete the current eth0 connection so that ubuntu will rediscover the wired connection?

---

