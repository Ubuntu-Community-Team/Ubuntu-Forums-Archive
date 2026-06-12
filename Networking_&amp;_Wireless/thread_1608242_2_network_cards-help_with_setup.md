---
title: "2 network cards-help with setup"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by johnhdsi on 2010-10-28
Hi all,
I am trying to get 2 network cards working at the same time. The first is a motherboard nic and i have no issues with it, the second is a Linksys LNE100TX. What I want to be able to do is to have the motherboard one (Eth0) for internet access and the Linksys (Eth1) for loading software via ethernet. In windows I have eth0 set to assign ip automatically for internet and Eth1 set to a static ip for my software loading. When I look at the network connections I see only 1 connection. I ran ifconfig and this is what I got


eth0      Link encap:Ethernet  HWaddr   
          inet addr:192.168.1.99  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:feae:2dc8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:82031 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16447689 (16.4 MB)  TX bytes:2319436 (2.3 MB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr  
          inet6 addr: fe80::222:6bff:fec3:ceee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:147 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6317 (6.3 KB)  TX bytes:19249 (19.2 KB)
          Interrupt:18 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4098 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4098 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:317713 (317.7 KB)  TX bytes:317713 (317.7 KB)
 when I run lspci I get 

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
04:02.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)

How would I go about setting this up so I can use both at the same time? if I enable Eth1 then I lose my internet connection so I am sure there is something I am missing here. Any info/help would be greatly appreciated.

Thanks in advance!!!
John

---

### Post by SeijiSensei on 2010-10-28
> **johnhdsi said:**
> How would I go about setting this up so I can use both at the same time? if I enable Eth1 then I lose my internet connection

In the static configuration for eth1, don't declare a gateway.  Your computer should have only one default gateway, and that's the router that connects to the Internet.

If you don't have a gateway declaration for eth1, or if removing it doesn't fix the problem, post the results of "route -n".

---

### Post by johnhdsi on 2010-10-28
here is the output

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


I don't have eth1 running right now because it's not available. What am I missing here?

---

### Post by SeijiSensei on 2010-10-28
Was there a gateway declaration for eth1 in /etc/network/interfaces?  Did you remove it?  It doesn't help to see the routing table if you don't have both interfaces active.

---

### Post by johnhdsi on 2010-10-28
I'm sorry about that, I didn't understand where to look. I will look in there first thing tomorrow when I get back to work. I do appreciate the help, please bear with me, I'm still new to networking in linux.

---

### Post by johnhdsi on 2010-10-29
here is the info from the interfaces file in the /etc/network/interfaces file



auto lo
iface lo inet loopback


I'm not sure I'm looking at what you were asking about still. I'm sorry for the back n forth, I'm new to this stuff and still confused on it.

---

### Post by SeijiSensei on 2010-10-29
I think I misread your initial comment.  It sounds like you can get both interfaces to work in Windows but not Ubuntu?  

Here's how to create the same static configuration for eth1 in Ubuntu.  Suppose you want to assign the static address 192.168.2.1.  Then you'd change /etc/network/interfaces to look like this:

```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
     address 192.168.2.1
     network 192.168.2.0
     netmask 255.255.255.0
     broadcast 192.168.2.255

```

Replace the address information with the same settings you used in Windows, then reboot.  Make sure the address is not in the same space as used by eth0, in your case not in 192.168.1.1-255.  It obviously has to be compatible with the address of your software archive, too.

---

### Post by johnhdsi on 2010-10-30
Ok, I added the code you posted to the file and here's what happens.

I lose the network notify icon on the top toolbar and I lose my internet connection. When I do an Ifconfig before the edit I get this 

eth0      Link encap:Ethernet  HWaddr 00:11:43:ae:2d:c8  
          inet addr:192.168.1.99  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:feae:2dc8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:670282 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9045 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:61188438 (61.1 MB)  TX bytes:1897661 (1.8 MB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:22:6b:c3:ce:ee  
          inet6 addr: fe80::222:6bff:fec3:ceee/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:4 dropped:0 overruns:0 carrier:8
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)


after the edit this is my output of ifconfig

eth0      Link encap:Ethernet  HWaddr 00:11:43:ae:2d:c8  
          inet6 addr: fe80::211:43ff:feae:2dc8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:577 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45327 (45.3 KB)  TX bytes:492 (492.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:22:6b:c3:ce:ee  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::222:6bff:fec3:ceee/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:3 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B

I left the static IP you had in there only for testing reasons (I figured it was easier for comparison purposes). So it would appear that now my Eth1 is up and running but Eth0 is not. Am I missing something? Thanks for all of the help with this I really appreciate it!

john

---

### Post by SeijiSensei on 2010-10-31
Add in the eth0 declaration as well, then:

```

auto lo
iface lo inet loopback 

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
     address 192.168.2.1
     network 192.168.2.0
     netmask 255.255.255.0
     broadcast 192.168.2.255

```

Is that better?

---

### Post by johnhdsi on 2010-11-03
worked like a charm!!!  thank you so much for the help!!:guitar:

I am assuming that if I require a different ip on Eth1 i can always edit out the lines in /interfaces that you had me add correct?

thank you again for the help, people like you are the reason that this forum is such a great resource for all of us noobs.

John

---

### Post by SeijiSensei on 2010-11-03
> **johnhdsi said:**
> I am assuming that if I require a different ip on Eth1 i can always edit out the lines in /interfaces that you had me add correct?

Yes, just make sure the all the IP information is consistent.   

> thank you again for the help, people like you are the reason that this forum is such a great resource for all of us noobs.

John

You're welcome, John!  Welcome to the world of Linux.

---

