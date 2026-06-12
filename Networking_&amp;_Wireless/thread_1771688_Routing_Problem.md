---
title: "Routing Problem"
date: 2011-05-30
forum: Networking &amp; Wireless
---

### Post by JKyleOKC on 2011-05-30
I have a strange problem. Whenever I have to restart this box, such as after a kernel update, my gateway to the outside world disappears.

Here's the definition in /etc/network/interfaces:```
iface eth1 inet static
#	pre-up /usr/sbin/ethtool -s eth1 autoneg off
	address xxx.143.22.33
	netmask 255.255.255.248
	gateway xxx.143.22.38

auto eth1

```And here's what happens when I test```
jk@mehitabel:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.143.22.32    *               255.255.255.248 U     0      0        0 eth1
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.0.2     0.0.0.0         UG    100    0        0 eth0
default         adsl-xxx-143-22- 0.0.0.0         UG    100    0        0 eth1
[COLOR="Red"]jk@mehitabel:~$ ping -c3 www.google.com
ping: unknown host www.google.com[/COLOR]
[COLOR="RoyalBlue"]jk@mehitabel:~$ sudo route add default gw xxx.143.22.38[/COLOR]
jk@mehitabel:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.143.22.32    *               255.255.255.248 U     0      0        0 eth1
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
[COLOR="Red"]default         adsl-xxx-143-22- 0.0.0.0         UG    0      0        0 eth1[/COLOR]
default         192.168.0.2     0.0.0.0         UG    100    0        0 eth0
default         adsl-xxx-143-22- 0.0.0.0         UG    100    0        0 eth1
jk@mehitabel:~$ ping -c3 www.google.com
PING www.l.google.com (74.125.227.17) 56(84) bytes of data.
64 bytes from 74.125.227.17: icmp_seq=1 ttl=52 time=19.0 ms
64 bytes from 74.125.227.17: icmp_seq=2 ttl=54 time=26.0 ms
64 bytes from 74.125.227.17: icmp_seq=3 ttl=52 time=19.5 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 19.090/21.585/26.078/3.185 ms

```The first part in red above indicates that I'm not getting out to the DSL modem in order to do the DNS lookup. Adding another "route" command to establish the default gateway (shown in blue) makes everything work properly, as shown by the ping result.

However I now have two default gateways, to the same IP, for the same interface, but with different metrics values (which as you can see I did not define with my command). My question is simply "What is causing this problem, and how can I prevent it on future restarts?"

Note: I'm not using Network Manager at all and have purged it from the system; the box has two NICs and serves as my router for my LAN. This is the only known problem in its networking configurations.

---

### Post by redmk2 on 2011-05-30
> **JKyleOKC said:**
> I have a strange problem. Whenever I have to restart this box, such as after a kernel update, my gateway to the outside world disappears.

Here's the definition in /etc/network/interfaces:```
iface eth1 inet static
#	pre-up /usr/sbin/ethtool -s eth1 autoneg off
	address xxx.143.22.33
	netmask 255.255.255.248
	gateway xxx.143.22.38

auto eth1

```And here's what happens when I test```
jk@mehitabel:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.143.22.32    *               255.255.255.248 U     0      0        0 eth1
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.0.2     0.0.0.0         UG    100    0        0 eth0
default         adsl-xxx-143-22- 0.0.0.0         UG    100    0        0 eth1
[COLOR="Red"]jk@mehitabel:~$ ping -c3 www.google.com
ping: unknown host www.google.com[/COLOR]



[COLOR="RoyalBlue"]jk@mehitabel:~$ sudo route add default gw xxx.143.22.38[/COLOR]
jk@mehitabel:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.143.22.32    *               255.255.255.248 U     0      0        0 eth1
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
[COLOR="Red"]default         adsl-xxx-143-22- 0.0.0.0         UG    0      0        0 eth1[/COLOR]
default         192.168.0.2     0.0.0.0         UG    100    0        0 eth0
default         adsl-xxx-143-22- 0.0.0.0         UG    100    0        0 eth1
jk@mehitabel:~$ ping -c3 www.google.com
PING www.l.google.com (74.125.227.17) 56(84) bytes of data.
64 bytes from 74.125.227.17: icmp_seq=1 ttl=52 time=19.0 ms
64 bytes from 74.125.227.17: icmp_seq=2 ttl=54 time=26.0 ms
64 bytes from 74.125.227.17: icmp_seq=3 ttl=52 time=19.5 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 19.090/21.585/26.078/3.185 ms

```The first part in red above indicates that I'm not getting out to the DSL modem in order to do the DNS lookup. Adding another "route" command to establish the default gateway (shown in blue) makes everything work properly, as shown by the ping result.

However I now have two default gateways, to the same IP, for the same interface, but with different metrics values (which as you can see I did not define with my command). My question is simply "What is causing this problem, and how can I prevent it on future restarts?"

Note: I'm not using Network Manager at all and have purged it from the system; the box has two NICs and serves as my router for my LAN. This is the only known problem in its networking configurations.

Hi Jim,

I have questions with this right off the bat.
[LIST=1]
[*]Are you pinging from the multihomed host (router)?
[*]Why do you need 2 gateways on this router? 
[/LIST]
Why do you need a "downstream" gateway (to the 192.168.0.0/24 net)?  How many hosts are on the xxx.143.22.32/29 net?

My understanding is that you assign a Default GW to an interface of a local host in the network.  Thus enabling any traffic that has an unknown or non-local destination to be sent sent to the GW interface.  Another way of putting it is:  The GW is the LAN side interface of the router (as seen by the local host).  

I believe you should not have 2 GW on any host (router or not) let alone have 2 GW on one interface. 

Are you sure you are loosing connectivity to the internet?  Could you ping the Google site by IP address and not by DNS name?

---

### Post by JKyleOKC on 2011-05-30
Yes, the pings are from the router, which I also use as a server and as my primary workstation. The router action all takes place in the background. I've been operating like this for nine years now, and this problem did not arise until sometime in the past year (after several kernel upgrades; under Hardy and the old mandrake 8.1 system, it was problem-free).

Each NIC needs its own gateway; eth1 is connected (through a hub) to the DSL modem while eth0 connects to an external 8-port switch that the other machines on my LAN get their signals from. For example, my Email client runs in a VM on another machine at 192.168.0.52, so incoming Email comes into the router box on eth1 through its gateway, and is forwarded to 192.168.0.52 through eth0 and its gateway. That's why I need the "downstream" gateway defined.

I can ping any machine on the LAN through the 192.168.0.2 gateway (that's the address of the router box itself), both by IP address and by name since I have my LAN hosts all entered in the /etc/hosts file.

However I cannot ping any external addresses through eth1, until I add the second default gateway manually. This is true both using the IP, and the name, of the external site such as Google.

I discovered that adding the default gateway a second time was a cure for the problem wholly by accident. I could ping the xxx.143.22.38 address, but nothing else; this implied to me that the gateway was not functioning so I added it by hand, and suddenly everything worked.

The xxx.143.22.32 subnet has five static IPs assigned by my ISP; I actually use only three of them and the other two (which also connect to the modem through the hub to allow use of all the IPs) do not respond to pings. The other three possible IPs in this subnet are the network address itself, the gateway address, and the broadcast address.

I'm beginning to believe that the difference in "metrics" values may be involved, since that's the only visible difference between the two eth1 default gateways shown by output of the "route" command. However I've still not formulated a strategy for testing this conclusion...

Thanks for the response!

---

### Post by redmk2 on 2011-05-31
> **JKyleOKC said:**
> Yes, the pings are from the router, which I also use as a server and as my primary workstation. The router action all takes place in the background. I've been operating like this for nine years now, and this problem did not arise until sometime in the past year (after several kernel upgrades; under Hardy and the old mandrake 8.1 system, it was problem-free).

That doesn't mean that the original configuration is the correct way of do things.  How many times have we seen an update uncover a misconfiguration.> 

Each NIC needs its own gateway; eth1 is connected (through a hub) to the DSL modem while eth0 connects to an external 8-port switch that the other machines on my LAN get their signals from. For example, my Email client runs in a VM on another machine at 192.168.0.52, so incoming Email comes into the router box on eth1 through its gateway, and is forwarded to 192.168.0.52 through eth0 and its gateway. That's why I need the "downstream" gateway defined.

A GW is just a transit point *[COLOR="Green"]**between 2 networks **[/COLOR]*.  it could be router to router.  A [**_[COLOR="Blue"]Default GW[/COLOR]_**]("http://en.wikipedia.org/wiki/Default_gateway") is needed when an IP packet's destination address belongs to someplace *[COLOR="Purple"]outside[/COLOR]* the local subnet. To my way of thinking neither of those descriptions match your situation when you ping a host from your router.  For example the router could be considered local to the network 192.168.0.0/24 since it has an interface in that LAN.  On the other hand it could also be a local node int the x.143.22.32/28 network.  I wonder if how you handle the routing (forwarding) has anything to do with this dilemma. > 

I can ping any machine on the LAN through the 192.168.0.2 gateway (that's the address of the router box itself), both by IP address and by name since I have my LAN hosts all entered in the /etc/hosts file.

What happens if you take away the GW on 192.168.0.2?  Can you ping 192.168.0.2 from 192.168.0.52?  Or visa versa?  What does the ARP cache hold.  All this communication should be at LAYER2 and both hosts should show up each others ARP cache.> 

However I cannot ping any external addresses through eth1, until I add the second default gateway manually. This is true both using the IP, and the name, of the external site such as Google.
Can you ping a host in the x.143.22.32/28 network from 192.168.0.52 or any other host in that network other than the router. > 

I discovered that adding the default gateway a second time was a cure for the problem wholly by accident. I could ping the xxx.143.22.38 address, but nothing else; this implied to me that the gateway was not functioning so I added it by hand, and suddenly everything worked.
I'll bet a default *route* would also do that (to the exclusion of all other hosts on that network).> 


The xxx.143.22.32 subnet has five static IPs assigned by my ISP; I actually use only three of them and the other two (which also connect to the modem through the hub to allow use of all the IPs) do not respond to pings. The other three possible IPs in this subnet are the network address itself, the gateway address, and the broadcast address.

Yes a /29 subnet contains 8 IP addresses with 6 available for hosts in the network.  The interface to your router is one of those hosts (a peer) it holds no special status when looking at the network from a LAN perspective.  The other 5 hosts should be able to ping that IP address (in this case x.143.22.33) and you should be able to ping them!  This has nothing to do with routing per say.  It does have a lot to do with how your IPtables is set up.  In this case the originating MAC and IP address for a ping could be important (i.e what network is the ping originating from.  Wireshark would be a good tool here.> 


I'm beginning to believe that the difference in "metrics" values may be involved, since that's the only visible difference between the two eth1 default gateways shown by output of the "route" command. However I've still not formulated a strategy for testing this conclusion...

Thanks for the response!

I short: origin, direction and destination of traffic is just as important as the proper use of GW and DGW.

All of this is just speculation and and the mutterings of a picky ol' S.O.B. who would always try an make it technically correct.  As a practical matter; if you can solve the problem with the set up you have, then GREAT!

---

### Post by JKyleOKC on 2011-05-31
> **redmk2 said:**
> That doesn't mean that the original configuration is the correct way of do things.  How many times have we seen an update uncover a misconfiguration.
I think this is another of those times! I've removed the eth0 gateway completely and deleted the added one from eth1, and everything still works. Have NOT restarted to verify, since there's another update package this morning that will probably require a restart. However three of the update files are still not present in the repository so I'm waiting for them before continuing...
> **redmk2 said:**
> What happens if you take away the GW on 192.168.0.2?  Can you ping 192.168.0.2 from 192.168.0.52?  Or visa versa?  What does the ARP cache hold.  All this communication should be at LAYER2 and both hosts should show up each others ARP cache.
Pinging both ways between 2 and 52 still works as it should. Didn't look at the ARP cache.
> **redmk2 said:**
> Can you ping a host in the x.143.22.32/28 network from 192.168.0.52 or any other host in that network other than the router. I'll bet a default *route* would also do that (to the exclusion of all other hosts on that network).Yes a /29 subnet contains 8 IP addresses with 6 available for hosts in the network.  The interface to your router is one of those hosts (a peer) it holds no special status when looking at the network from a LAN perspective.  The other 5 hosts should be able to ping that IP address (in this case x.143.22.33) and you should be able to ping them!  This has nothing to do with routing per say.  It does have a lot to do with how your IPtables is set up.Iptables on this box allows pings; the other two hosts on the 143 subnet are set up to ignore ping requests; one is Win XP Pro and the other is a Linksys WRT54GL wireless router. Incidentally only 5 addresses are available, not 6 (unless you count the ISP's gateway address at 38 as one of the hosts). The machine at 52 can ping the 143.22.38 ISP gateway, though. It can also ping Google, and that has to go through the one at 2 to get to the ISP, so I'm confident that the setup is now in better shape. This is after removing the excess defaults from the router box.
> **redmk2 said:**
>   In this case the originating MAC and IP address for a ping could be important (i.e what network is the ping originating from.  Wireshark would be a good tool here.

I short: origin, direction and destination of traffic is just as important as the proper use of GW and DGW.Absolutely! The setup with different default gateways came directly out of one of the HOW-TO documents I studied when first setting this up way back there, using Mandrake 8.1 on an ancient Pentium II box with just 80 MiB of RAM, and then copied on every system change.
> **redmk2 said:**
> All of this is just speculation and and the mutterings of a picky ol' S.O.B. who would always try an make it technically correct.  As a practical matter; if you can solve the problem with the set up you have, then GREAT!It looks as if you may have nailed it. I'll hold off marking the thread as solved, though, until I see whether it survives a restart. In the meantime I've modified my /etc/network/interfaces file to comment out the gateway for eth0, and added a "metrics 10" line to the eth1 stanza.

Many thanks!

EDIT: Rebooted after the update and everything works properly now. Problem solved!

---

### Post by redmk2 on 2011-05-31
> **JKyleOKC said:**
> ...Incidentally only 5 addresses are available, not 6 (unless you count the ISP's gateway address at 38 as one of the hosts).

You do count it as a available IP address.  The only non assignable IP addresses are the NetID and the broadcast IP addresses. A gateway address is the IP address of a host in the LAN that it resides in.  Routers are hosts.  I have a router (bb-gw1) a wireless AP (bb-ap1) and a printer (bb-hp1).  All are hosts in the LAN.   >  

...Rebooted after the update and everything works properly now. Problem solved!

Many thanks!


I'm glad it worked out.  These kind of things have the potential to be frustrating and time consuming.

-Red

---

### Post by JKyleOKC on 2011-05-31
> **redmk2 said:**
> These kind of things have the potential to be frustrating and time consuming.

-RedI think that qualifies as the understatement of the year. Now I wonder how much other cruft infests my systems...

---

### Post by redmk2 on 2011-05-31
> **JKyleOKC said:**
> I think that qualifies as the understatement of the year. Now I wonder how much other cruft infests my systems...

That is the problem with following anyone's tutorial.  The things misunderstood and accidentally left out can be frightening.  I usually figure out what I need from the man pages and bits found on the web.  

I believe that it is impossible to *know all* in the world of computing.  After a while you find individuals whom you trust regarding the things you are not so familiar with.

---

