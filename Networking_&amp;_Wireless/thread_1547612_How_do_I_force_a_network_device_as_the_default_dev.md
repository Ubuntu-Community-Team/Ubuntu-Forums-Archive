---
title: "How do I force a network device as the default device?"
date: 2010-08-07
forum: Networking &amp; Wireless
---

### Post by jdmcmillian on 2010-08-07
My server (ubuntu-server-64-10.04) has two network cards installed, eth0 and eth1 installed respectively on two seperate networks, green and blue (ip-cop firewall).  Every now and then, the server trys to process all outgoing communication through eth1, which has no internet connectivity.  if I "ifdown eth1", this forces it to work through eth0 which works fine, but takes the server off the blue network which I dont want, I can bring the device back up and things are fine, but after a while ( assuming the dhcp lease time ) it reverts back to eth1, and has to be reset again as described above.

ifconfig[INDENT] eth0      Link encap:Ethernet  HWaddr 00:1c:c0:24:39:9f
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe24:399f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26392481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40669246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:24631512840 (24.6 GB)  TX bytes:47858492417 (47.8 GB)
          Memory:e8480000-e84a0000

eth1      Link encap:Ethernet  HWaddr 00:1b:2f:cf:0f:58
          inet addr:192.168.2.164  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:2fff:fecf:f58/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99043574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70538292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:122518573927 (122.5 GB)  TX bytes:36486514563 (36.4 GB)
          Interrupt:22 Base address:0x4800
[/INDENT]/etc/network/interface[INDENT]auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
[/INDENT]Any advice on how to force the server to use ETH0 for all server originate communication?

Thanks.

---

### Post by jdmcmillian on 2010-08-16
bump...

---

### Post by jdmcmillian on 2010-08-23
Did I post this in the wrong place???

---

### Post by Iowan on 2010-08-23
This would seem to be the appropriate place...
A "gateway" line (listing router address) in eth0 definition *should* point all non-internal traffic through eth0. This should show up under **route -n** with a UG for the gateway.

---

### Post by jdmcmillian on 2010-08-25
Iowan: First, thank you for replying, I was beginning to worry there was  no answer and my machine just didn't like me.

> **Iowan said:**
> This  would seem to be the appropriate place...
A "gateway" line (listing router address) in eth0 definition *should*  point all non-internal traffic through eth0. This should show up under **route  -n** with a UG for the gateway.


Here's  'route' and 'route -n'

**route**
[INDENT]Kernel  IP routing table
Destination     Gateway         Genmask          Flags Metric Ref    Use Iface
192.168.2.0     *                255.255.255.0   U     0      0        0 eth1
192.168.1.0      *               255.255.255.0   U     0      0        0 eth0
default          192.168.2.1     0.0.0.0         UG    100    0        0 eth1
default          firewall.home   0.0.0.0         UG    100    0        0 eth0
[/INDENT]
**route  -n**
[INDENT]Kernel IP routing table
Destination      Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0      0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.1.0      0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0          192.168.2.1     0.0.0.0         UG    100    0        0 eth1
0.0.0.0          192.168.1.1     0.0.0.0         UG    100    0        0 eth0
[/INDENT]

So  I'm thinking I need to get rid of this line:
[INDENT]**0.0.0.0          192.168.2.1     0.0.0.0         UG    100    0        0  eth1**

[/INDENT]so how do I get rid of that route at start up?   I've already looked in 'man route' and tracked down that i likely(???)  need to make a changed to '**/etc/network/interfaces**'  But I cant seem to  pin down what to do to remove the entry at boot time.  And at the same  time I want to ensure that the system can continue to talk to  192.168.2.X as needed while sending all internet traffic through  192.168.1.1


ok... so what I did was this, I added
[INDENT]**up  route del -net 0.0.0.0 gw 192.168.2.1**

[/INDENT]to   '**/etc/network/interfaces**' at the tail end of the '**eth1**' section and  restarted the machine, it seems to have removed the entry in question.   Is this the behavior I want? I seems to me that the entry is removed  after being added, is there a way to prevent it from being added to  begin with?


Again, thank you for your answer.

~jd

---

### Post by BkkBonanza on 2010-08-25
You might try manually setting the gateway values in your interfaces file. This may force it to only add a single gateway route. I don't have two interfaces here now so I can't try this out, but it seems plausible.
eg.

/etc/network/interface

    auto lo
    iface lo inet loopback

    # The primary network interface
    auto eth0
    iface eth0 inet dhcp
    gateway 192.168.1.1

    auto eth1
    iface eth1 inet dhcp
    gateway 192.168.1.1

---

### Post by Iowan on 2010-08-25
Two gateways are usually a problem - that's where "other traffic" should go. If eth0 is the internet-facing interface - it should *probably* be the gateway. Try setting it in */etc/network/interfaces* - if it doesn't help, it's not hard to remove...

---

### Post by LishyGuy on 2010-08-25
I'm having the same problem, but on Desktop edition, and between eth0 and wlan0.  My wireless interface connects to the router, but when I plug a crossover cable into eth0 to connect my netbook with my pc, it seems to be making internet requests through that instead.

Changing the gateway of eth0 to the same one as wlan0 didn't help, however I did it in Network Connections instead of manually editing /etc/network/interfaces, because that seems to be empty apart from the loopback interface.

---

### Post by jdmcmillian on 2010-09-03
I wanted to touch base and close this thread out, it seems that I've a working solution now.

I set the concerned devices to manual and static.  and added a routeing command to the networking interfaces file.... see  my interfaces file below....

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.1.3
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255
    gateway 192.168.1.1

auto eth1
iface eth1 inet static
    address 192.168.2.3
    network 192.168.2.0
    netmask 255.255.255.0
    broadcast 192.168.2.255
    gateway 192.168.2.1
    up route del -net 0.0.0.0 gw 192.168.2.1

```the final up route command deletes the routing information from eth1 when the network interface is brought up.  Its been running for a week no with no problem, if it fails, i'll repoen the thread.

---

