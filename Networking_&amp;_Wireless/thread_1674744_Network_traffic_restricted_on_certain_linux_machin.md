---
title: "Network traffic restricted on certain linux machines"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by marli on 2011-01-24
Okay, first, here is our setup:

Linksys Router with firewall
1 Linux Server -- Running Dapper
Multiple Linux ThinClients running off the linux server
Multiple Freestanding Linux Machines -- Running ubuntu variants
Multiple Freestanding Windows Machines -- Running windows variants


The issue is that certain websites will not load on the freestanding linux machines, but they will load on our linux server and all the windows machines.

examples:  adobe.com, acer.com

These sites will start to load, but they never really finish and just seem to time out.

I have tried changing the dns on the freestanding linux laptops to use 208.67.220.220 and this does not solve the problem.

I have checked the firewall rules and they seem pretty standard.

When the linux machines are used on other networks, these websites work, so the problem seems to be related to this particular network.

When I do (freestanding linux): ```
traceroute acer.com -I
```
The trace times out at 30 hops

When I do (linux server): ```
traceroute acer.com -I
```
The trace reaches the destination at 19 hops

Both of the traceroute requests start by going through the router.

So the big issue is that websites will load on our linux server and all our windows machines, but not on freestanding linux clients.

Any ideas??  I didn't setup our original network and this is driving me crazy trying to figure it out. Any help would really be appreciated.

-- marli

---

### Post by SeijiSensei on 2011-01-24
Are all the machines in the same IP subnet?  Perhaps some of them are getting addresses that aren't correctly masqueraded by the router? 

If they're not all in the same subnet (and managed by the router), there has to be some other machine providing routing on the network.  Maybe it's misconfigured?

---

### Post by marli on 2011-01-24
All the machines have ip's of the form 192.168.0.xxx with subnet mask of 255.255.255.0

On my laptop for example (dual boot):

Windows XP (all sites work):
IP: 192.168.0.134
subnet mask: 255.255.255.0
gateway: 192.168.0.254    <-- router ip
dhcp: 192.168.0.64        <-- main linux server ip
dns: 192.168.0.64         


Ubuntu (most sites work, but not all):
IP: 192.168.0.123
subnet mask: 255.255.255.0
route (gateway): 192.168.0.254
dhcp: 192.168.0.64
dns: 208.67.220.220


Does this look okay? I didn't see anything out of the ordinary, but I'm no expert on this.  Any other settings I should check?


I've tried alternate dns servers with no improvement.
Also, the web browser doesn't change the result either.  I've tried in epiphany, firefox, and elinks with the same result.
And alternative versions of linux are also blocked.  I'm running 10.04, but 10.10 netbook and older versions have been blocked too.

I believe squid is running on our main linux server, would this somehow interfere?  Would all traffic would need to be routed through the linux server for this to have an impact?

I may try updating our router firmware this evening, could this help?

---

### Post by marli on 2011-01-25
Here is the result of "route print" in windows:

```
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 23 5a 4b 95 a3 ...... Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Cont
roller - Packet Scheduler Miniport
0x3 ...00 24 2b 52 cc c6 ...... Atheros AR5007EG Wireless Network Adapter - Pack
et Scheduler Miniport
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0    192.168.0.254   192.168.0.134       20
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
      192.168.0.0    255.255.255.0    192.168.0.134   192.168.0.134       20
    192.168.0.134  255.255.255.255        127.0.0.1       127.0.0.1       20
    192.168.0.255  255.255.255.255    192.168.0.134   192.168.0.134       20
        224.0.0.0        240.0.0.0    192.168.0.134   192.168.0.134       20
  255.255.255.255  255.255.255.255    192.168.0.134               3       1
  255.255.255.255  255.255.255.255    192.168.0.134   192.168.0.134       1
Default Gateway:     192.168.0.254
===========================================================================
Persistent Routes:
  None

```

---

### Post by marli on 2011-01-25
And here is my "route" info from ubuntu:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.0.254   0.0.0.0         UG    0      0        0 eth0

```

Anything look fishy here?

I am pretty much out of ideas of how to fix this problem if anyone can help?

---

