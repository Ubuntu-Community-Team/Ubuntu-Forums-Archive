---
title: "fixed routable ip cannot access the internet"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by nickfromnt77 on 2010-07-14
I've been banging my head against the wall now for 3 days.  I wonder if anyone else has had a problem similar to this.

Recently I purchased an Asus RS100-E5-P12 server.  It has 2 internal Broadcom BCM5721 NICs in it.  I decided to install 10.4 on it.  The goal is to make it a gateway for my network.

When I try to set one of the NICs with my fixed routable ip (98.174.228.244), I have no access the the internet.  I'll add here that my other server when using the same IP, does have access to the internet (note that I don't use the same ip on both boxes at the same time - I just did a test with the other server).  It's running 9.10.  

Ifconfig prints this:[INDENT]**[FONT=Courier New]nick@nsg1:~$ sudo ifconfig[/FONT]**
**[FONT=Courier New]eth0      Link encap:Ethernet  HWaddr e0:cb:4e:44:09:88  [/FONT]**
**[FONT=Courier New]          inet addr:98.174.228.244  Bcast:98.174.228.255  Mask:255.255.255.240[/FONT]**
**[FONT=Courier New]          inet6 addr: fe80::e2cb:4eff:fe44:988/64 Scope:Link[/FONT]**
**[FONT=Courier New]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT]**
**[FONT=Courier New]          RX packets:5838 errors:0 dropped:0 overruns:0 frame:0[/FONT]**
**[FONT=Courier New]          TX packets:166 errors:0 dropped:0 overruns:0 carrier:0[/FONT]**
**[FONT=Courier New]          collisions:0 txqueuelen:1000 [/FONT]**
**[FONT=Courier New]          RX bytes:418535 (418.5 KB)  TX bytes:11952 (11.9 KB)[/FONT]**
**[FONT=Courier New]          Interrupt:11 [/FONT]**

**[FONT=Courier New]eth1      Link encap:Ethernet  HWaddr e0:cb:4e:44:09:56  [/FONT]**
**[FONT=Courier New]          inet addr:192.168.54.1  Bcast:192.168.54.255  Mask:255.255.255.0[/FONT]**
**[FONT=Courier New]          inet6 addr: fe80::e2cb:4eff:fe44:956/64 Scope:Link[/FONT]**
**[FONT=Courier New]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT]**
**[FONT=Courier New]          RX packets:713 errors:0 dropped:0 overruns:0 frame:0[/FONT]**
**[FONT=Courier New]          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0[/FONT]**
**[FONT=Courier New]          collisions:0 txqueuelen:1000 [/FONT]**
**[FONT=Courier New]          RX bytes:137478 (137.4 KB)  TX bytes:18854 (18.8 KB)[/FONT]**
**[FONT=Courier New]          Interrupt:10 [/FONT]**

**[FONT=Courier New]lo        Link encap:Local Loopback  [/FONT]**
**[FONT=Courier New]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT]**
**[FONT=Courier New]          inet6 addr: ::1/128 Scope:Host[/FONT]**
**[FONT=Courier New]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT]**
**[FONT=Courier New]          RX packets:82 errors:0 dropped:0 overruns:0 frame:0[/FONT]**
**[FONT=Courier New]          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0[/FONT]**
**[FONT=Courier New]          collisions:0 txqueuelen:0 [/FONT]**
**[FONT=Courier New]          RX bytes:7600 (7.6 KB)  TX bytes:7600 (7.6 KB)[/FONT]**
[/INDENT]The interfaces file looks like this:[INDENT]a**[FONT=Courier New]uto lo[/FONT]**
**[FONT=Courier New]iface lo inet loopback[/FONT]**

**[FONT=Courier New]auto eth0[/FONT]**
**[FONT=Courier New]iface eth0 inet static[/FONT]**
**[FONT=Courier New]address 98.174.228.244[/FONT]**
**[FONT=Courier New]netmask 255.255.255.240[/FONT]**
**[FONT=Courier New]gateway 98.174.228.241[/FONT]**
**[FONT=Courier New]network 98.174.228.0[/FONT]**

**[FONT=Courier New]auto eth1[/FONT]**
**[FONT=Courier New]iface eth1 inet static[/FONT]**
**[FONT=Courier New]address 192.168.54.1[/FONT]**
**[FONT=Courier New]netmask 255.255.255.0[/FONT]**
[/INDENT]If anyone can point me to some resource to solve this problem, I'd be forever grateful!

---

### Post by Iowan on 2010-07-15
You can't access internet *from the server*? To what does the "Internet" interface connect? Some modems "lock onto" a MAC address, and must be reset before they will work with another one.

---

### Post by YesWeCan on 2010-07-15
What does your kernel routing table contain?
'route -n'

@Iowan: Yes, my modem needs power-cycling if I change the NIC it connects to. I am curious as to how the NIC/modem interface works - should the modem do dhcp for the NIC or if the NIC has a static address how does the modem know what it is?

---

### Post by nickfromnt77 on 2010-07-15
> **Iowan said:**
> You can't access internet *from the server*? To what does the "Internet" interface connect? Some modems "lock onto" a MAC address, and must be reset before they will work with another one.

That's correct.  When I try to ping either the gateway or the name servers, I get 'destination host unreachable'.  I can ssh into the server and I can ping it from a different host on the local network.

From what I've read, I'm guessing the routing table isn't correct and I don't know much about route - I've never been in this situation before.

---

### Post by nickfromnt77 on 2010-07-15
> **YesWeCan said:**
> What does your kernel routing table contain?
'route -n'

@Iowan: Yes, my modem needs power-cycling if I change the NIC it connects to. I am curious as to how the NIC/modem interface works - should the modem do dhcp for the NIC or if the NIC has a static address how does the modem know what it is?

Route returns:
nick@nsg1:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
98.174.228.240  0.0.0.0         255.255.255.240 U     0      0        0 eth0
192.168.54.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         98.174.228.241  0.0.0.0         UG    100    0        0 eth0

---

### Post by YesWeCan on 2010-07-15
Would you be more specific about which machine can or can't ping what from where on what IP address?
What happens when you 'ping 74.125.47.105' (google.com) from the server itself?
IOW does the default gateway 98.174.228.241 via eth0 function for the server itself?

---

### Post by nickfromnt77 on 2010-07-15
> **YesWeCan said:**
> Would you be more specific about which machine can or can't ping what from where on what IP address?
What happens when you 'ping 74.125.47.105' (google.com) from the server itself?
IOW does the default gateway 98.174.228.241 via eth0 function for the server itself?


@Iowan: Cycling the power on the modem worked!  I've got to admit, I'm totally surprised.  I was expecting massive learning curves manually setting up the routing table.

---

### Post by Skaperen on 2010-07-15
> **nickfromnt77 said:**
> @Iowan: Cycling the power on the modem worked!  I've got to admit, I'm totally surprised.  I was expecting massive learning curves manually setting up the routing table.
Ways to have debugged this include (if you still want some learning curve) noticing no ping replies from the gateway (98.174.228.241) should work on getting this fixed first.  On the previous machine that worked, get the MAC address of the modem from "arp -n".  On the new machine that does not, check "arp -n" to see if the MAC even shows.  Try a different IP if you have one, to see if the modem would work with that.

But, yeah, cheap hardware is very often a culprit.  Its ARP table might eventually expire (causing a new ARP query), but who knows when.

---

### Post by nickfromnt77 on 2010-07-15
> **Skaperen said:**
> Ways to have debugged this include (if you still want some learning curve) noticing no ping replies from the gateway (98.174.228.241) should work on getting this fixed first.  On the previous machine that worked, get the MAC address of the modem from "arp -n".  On the new machine that does not, check "arp -n" to see if the MAC even shows.  Try a different IP if you have one, to see if the modem would work with that.

But, yeah, cheap hardware is very often a culprit.  Its ARP table might eventually expire (causing a new ARP query), but who knows when.


Good one.  I never even thought about using arp.  Low level networking is pretty much a mystery to me.

---

