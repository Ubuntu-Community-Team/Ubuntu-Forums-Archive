---
title: "ethernet card not working in 10.04 server"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by Grimfel on 2010-07-18
Hi,

I'll preface with:

I'm abslutely brand new to linux, please bear with me.

I've set up 10.04 Server so that I could install directly to a command line, due to the fact that Desktop was crashing during the install every time. The installation goes fine, except for the networking portion.

DHCP fails every time I try it. So I set up a static IP as an alternative.

Once installation completes, none of the network-oriented tools (ping, telnet) work. I've tried pinging my router and I get 'Destination Host Unknown'. This is true if I change to a DHCP oriented setup as well.

The router sees that the machine is there, as indicated by the slowly blinking connection light meaning that it's hooked up to *something* but there's no activity. Also, networking did work within Windows before I nuked it, so I know it has the ability to operate correctly.

I'm at a loss, mostly due to my own newness and ignorance of how to start tackling this within this environment.

Any help would be appreciated.

---

### Post by Iowan on 2010-07-18
A couple of things to check:
Are you pinging router by name or address? 
Post results (from a terminal) of **route -n** 
*/etc/resolv.conf* should contain the name of your nameserver.

---

### Post by Grimfel on 2010-07-19
> **Iowan said:**
> A couple of things to check:
Are you pinging router by name or address? 
Post results (from a terminal) of **route -n** 
*/etc/resolv.conf* should contain the name of your nameserver.

Thanks for the response.

I'm pinging my router by address, using 192.168.1.1

Here are the results of a route -n :

Destination    Gareway       Genmask         Flags Metric Ref   Use Iface
192.168.1.0   0.0.0.0          255.255.255.0  U      0        0      0    eth0
0.0.0.0          192.168.1.1   0.0.0.0             UG   100     0      0    eth0

---

### Post by Iowan on 2010-07-19
Silly question, I'm sure... but **ifconfig -a** shows eth0 with a 192.168.1.X address?

---

### Post by Grimfel on 2010-07-19
Yup. :)

IP Address is listed as 192.168.1.30

---

### Post by Iowan on 2010-07-19
:-k You're using up all my "easy" fixes...
Firewall rules? What are results of **iptables -L**?
BTW, I'm not sure how to fix firewall/iptables problems - since I'm not brave enough to suggest flushing them.

---

### Post by Grimfel on 2010-07-19
iptables -L gives me the following:

Chain INPUT )policy ACCEPT)
target prot opt source destination

Chain FORWARD and OUTPUT are identical to the above.

---

### Post by Iowan on 2010-07-19
Not a firewall problem...

What does **sudo lshw -C network** report about the interface?
(I'm wondering about driver...another weak area for me.)

---

### Post by Grimfel on 2010-07-19
*-network
description: Ethernet interface
product: 82801DB PRO/100 VE (LOM) Ethernet Controller
vendor: Intel Corporation
physical id: 8
bus info: pci@0000:01:08.0
logical name: eth0
version:82
serial: 00:07:d9f6:01:20
size: 10MB/s
capacity: 100MB/s
width 32 bits
clock: 33 MHz

capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonetgotiation

configuration: autonegotiation-on broadcast-yes driver-e100 driverversion-3.5.24-kZ-NAPI duplex=half firmware=N/A ip=192.168.1.30 latency=32 link-no malatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s

resources: irq:20 memory:ff8fe000-ff8fefff ioport:d880(size=65


I'm hoping there's no critical typos in there since I can't copy and paste, so I am my own clipboard. :)

---

### Post by Iowan on 2010-07-20
I'm running out of ideas, but thought a "bump" might be in order.  Did this machine connect "in a former life" (i.e. did it ever connect as a Windows machine)? Have you tried the connection on another machine? Since nothing else jumps out, I'm wondering if the cable might be bad or wrong  (crossover), or plugged into uplink port.

---

### Post by Grimfel on 2010-07-20
Yes. Under Windows XP, the previous operating system, the connection was fine. There's only one ethernet port on the machine, so no possibility of an up/down conflict. I've tried swapping the cable from my PS3 (which works) with this one and this box still fails while the PS3 works fine, so not a cable issue. I've also plugged this machine into the same port on the router that the PS3 is normally on, just in case the port on the router was bad, and when swapped at the router, the PS3 still works and this machine still fails.

The only thing I can think of (pure guessing, here, so not real technical) is that the system installed incorrect drivers for the box's ethernet. If that's the case, then what I would need help with is how to install the appropriate drivers, and how to do it without an internet connection.

I just want to make sure there's nothing else I should be doing before I start messing around with replacing drivers and potentially make the entire situation worse.

I'm good at that.

---

### Post by Grimfel on 2010-07-22
Sad, helpless, pathetic bump.

---

