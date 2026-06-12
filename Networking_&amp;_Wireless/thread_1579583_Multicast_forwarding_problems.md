---
title: "Multicast forwarding problems"
date: 2010-09-22
forum: Networking &amp; Wireless
---

### Post by nadavbitt on 2010-09-22
[FONT=Times New Roman][SIZE=3]Hello all[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]My name is Nadav and I’m new to linux. I have installed Ubuntu desktop OS my PC, and I’m trying to enable multicast forwarding between two network interfaces. Each is connected to different LAN. [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]PC configuration[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]NIC 1 configuration:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Name: Eth0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]IP: 192.168.0.1[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Subnet: 255.255.255.0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Default gateway: Unspecified[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]NIC 2 configuration:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Name: Eth1[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]IP: 193.168.0.1[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Subnet: 255.255.255.0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Default gateway: Unspecified[/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]IP Forwarding is enabled: I’m able to send IP traffic between computers on both end, for example ping between PC 192.168.0.2 gets reply from PC 193.168.0.5[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]End station gateway is configured to be the Linux box IP.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I have also installed PIMD and SMCROUTE.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I have also added the following routes commands[/SIZE][/FONT]
[FONT=Verdana]route add -net 224.0.0.0 netmask 240.0.0.0 dev eth0[/FONT]
[FONT=Verdana]route add -net 224.0.0.0 netmask 240.0.0.0 dev eth1[/FONT]
 
[FONT=Verdana]After doing all the above I still can’t send multicast traffic trough the linux box. [/FONT]
[FONT=Verdana]Using Wireshark I can see the multicast traffic is received by the Linux box but it is not being forward. [/FONT]
 
[FONT=Verdana]How do I configure the SMCROUTE or the PIMD to forward traffic between the two NIC’s?[/FONT]
[FONT=Verdana]Is there something I need to do with the IPTABLES?[/FONT]
 
[FONT=Verdana]Please if you can provide the commands that I need to add in order to send multicast traffic between two NIC’s[/FONT]
 
[FONT=Verdana]Beast regards Nadav[/FONT]

---

### Post by troglobit on 2010-11-20
Hi Nadav, sorry for the late reply!

There are a couple of gotchas that you need to remember when routing.  You already mentioned both the ip forwarding and routing, so you're obviously not new to networking.  However, for *multicast* routing there are a couple of additional things to remember:

[LIST=1]
[*]TTL.  What's the TTL of your multicast data?  You want it to be > 1 to be able to route more than one hop.
[*]Static multicast routes are not really needed when you run pimd, remove them and try again.
[/LIST]
If you run [pimd]("http://freshmeat.net/projects/pimd") (or [mrouted]("http://freshmeat.net/projects/mrouted"), which is even easier) you usually don't need to do much, pimd/mrouted are enabled by default on all interfaces.  As long as pimd receives an IGMP join (membership report) on the destination network the multicast group on the source network is forwarded.

I hope this helps!

---

