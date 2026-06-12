---
title: "Unable to connect to a home network."
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by Teilani on 2009-01-07
Hello.

I have recently downloaded and installed Ubuntu 8.1 on a PC I had laying around to try out Linux.

Long story short, I'm trying to connect to a network (Linksys Router)with a Via Rhine II Fast Ethernet Adapter.  It's not connecting at all.  Upon logging into the router the log shows that the computer hasn't even tried to connect.

Router is set up for DHCP and provides all computers in our home with an IP automatically.

Since this is a fresh install of Ubuntu, no settings have been changed at all.  Please keep in mind that I have read countless posts on this topic and have also read the manual supplied with Ubuntu.  While the manual makes references to things like "Network Settings", all I seem to be able to find is "Network Tools" and "Network Configuration".  Neither of which helps.  My questions are:

**How do you verify that the network adapter is installed properly?**

**How do you configure the adapter to access a network?**


Thank you in advance for any help you are able to provide.

**Teilani**

---

### Post by mikewhatever on 2009-01-07
Please post the outputs of the following commands:
> ifconfig
sudo lshw -C network

---

### Post by Teilani on 2009-01-07
ifconfig

eth0      
Link encap:Ethernet  
HWaddr 00:16:ec:a7:55:c1          
inet6 addr: fe80::216:ecff:fea7:55c1/64 
Scope:Link          
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1          
RX packets:4 errors:0 dropped:0 overruns:0 frame:0          
TX packets:30 errors:0 dropped:0 overruns:0 carrier:0          
collisions:0 txqueuelen:1000          
RX bytes:354 (354.0 B)  
TX bytes:8676 (8.6 KB)          
Interrupt:23 Base address:0xa000 

lo        
Link encap:Local Loopback         
inet addr:127.0.0.1  Mask:255.0.0.0        
inet6 addr: ::1/128 Scope:Host         
UP LOOPBACK RUNNING  MTU:16436  Metric:1         
RX packets:264 errors:0 dropped:0 overruns:0 frame:0        
TX packets:264 errors:0 dropped:0 overruns:0 carrier:0         
collisions:0 txqueuelen:0          
RX bytes:17292 (17.2 KB)  TX bytes:17292 (17.2 KB)


teilani@teilani-desktop:~$ sudo lshw -c network
*-network                      
description: Ethernet interface       
product: VT6102 [Rhine-II]       
vendor: VIA Technologies, Inc.       
physical id: 12       
bus info: pci@0000:00:12.0       
logical name: eth0       
version: 78       
serial: 00:16:ec:a7:55:c1       
size: 100MB/s       
capacity: 100MB/s       
width: 32 bits       
clock: 33MHz       
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s  
*-network DISABLED       
description: Ethernet interface       
physical id: 1       
logical name: pan0       
serial: de:bf:57:2c:cd:a9       
capabilities: ethernet physical       
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
teilani@teilani-desktop:~$

---

### Post by ptm on 2009-01-07
Here's what mine produced 

o run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

pt@compaqlaptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:02:93:33:68  
          inet6 addr: fe80::208:2ff:fe93:3368/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1836 (1.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:250 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15684 (15.6 KB)  TX bytes:15684 (15.6 KB)

pt@compaqlaptop:~$ sudo lshw -C network
[sudo] password for pt: 
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:08:02:93:33:68
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6a:5b:d9:c1:c9:92
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
pt@compaqlaptop:~$ 

:popcorn:

---

### Post by Teilani on 2009-01-07
Hmm, not sure why but the issue seems to have resolved itself.  Something I could never get Windows to do...QQ.  Im in love.

---

### Post by ptm on 2009-01-07
Sorry, I wish i could say the same.  When I tried to modify \Network\interfaces per the man pages i get the You don't have permission to modify this file.  Oh well.  :confused:

---

### Post by ptm on 2009-01-07
I stand corrected, it required that i put in a DNS server address which I was miscontruing as automagic.  My Bad.  :KS

---

### Post by Zack McCool on 2009-01-07
> **ptm said:**
> Sorry, I wish i could say the same.  When I tried to modify \Network\interfaces per the man pages i get the You don't have permission to modify this file.  Oh well.  :confused:

I know you now seem to have the trouble resolved, but on this point; to edit system files you need to precede the command with sudo to give yourself rights to the file.  For instance:

```
 sudo nano /etc/network/interfaces 
```

Will allow you to edit the file.  Without the sudo, you are a normal user, and aren't able to do that.

---

### Post by Teilani on 2009-01-07
Is there a comprehensive list of sudo commands?

---

