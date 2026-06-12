---
title: "routing help"
date: 2010-10-08
forum: Networking &amp; Wireless
---

### Post by giannir on 2010-10-08
Hi guys!

I have a firewall Ubuntu 10.04 with 3 nic interface (Wan, Dmz, Lan with Vlan tagging 8021q).

I would configure this machine with static routing between Vlan on ethint and ethdmz but I don't figure out how to do this infact I can't ping from Vlan to dmz and viceversa. 
 
If I add a static routing on windows machine on vlan "route add -p 172.18.110.0 mask 255.255.255.248 172.18.120.1" I can ping the firewall 172.18.110.1 but I can't ping the server 172.18.110.5 for example.

Now I don't want to apply this routing rules on all windows machine but I want add static routing on firewall so I can ping from Vlan the Dmz zone and viceversa.
 
FW
| --- ethext 192.xx.xx.xx
| --- ethdmz 172.18.110.0 
| --- ethint 172.18.120.0 (vlan id 120)

I want route all packets from interface vlan120 with destination 172.18.110.0 to ethdmz

This is my route command
Tabella di routing IP del kernel
Destination Gateway Genmask Flags Metric Ref Use Iface
10.8.0.2 * 255.255.255.255 UH 0 0 0 tun0
172.18.110.0 * 255.255.255.248 U 0 0 0 ethdmz
172.18.150.0 * 255.255.255.224 U 0 0 0 vlan150
172.18.90.0 * 255.255.255.224 U 0 0 0 vlan90
172.18.130.0 * 255.255.255.0 U 0 0 0 vlan130
10.8.0.0 10.8.0.2 255.255.255.0 UG 0 0 0 tun0
192.168.1.0 * 255.255.255.0 U 0 0 0 ethext
172.18.140.0 * 255.255.255.0 U 0 0 0 vlan140
172.18.120.0 * 255.255.252.0 U 0 0 0 vlan120
default 192.168.1.254 0.0.0.0 UG 100 0 0 ethext


Thanks all from helping me!

Regards
Gianni
 
PS I don't search for natting or bridging!

---

### Post by giannir on 2010-10-10
nobody can help me?

---

### Post by SeijiSensei on 2010-10-10
> **giannir said:**
> "route add -p 172.18.110.0 mask 255.255.255.248 172.18.120.1" I can ping the firewall 172.18.110.1 but I can't ping the server 172.18.110.5 for example.

I don't see a -p option in the man page for route.  What's it supposed to do?  I'd use either

route add -net 172.18.110.0 netmask 255.255.255.248 gw 172.18.120.1

or using the newer and simpler "ip" command

ip route add 172.18.110.0/29 via 172.18.120.1


Do either of these formats work for you?

---

### Post by giannir on 2010-10-12
Thanks for replying me!
 
The options -p is for route command on Winzozz and not under Linux! :)
 
I added the command route add -p 172.18.110.0 mask 255.255.255.248 172.18.120.1 on windows machine and I can ping the interface 172.18.110.1 on Linux firewall but I can't ping the machine 172.18.110.5.
 
Instead if I add the routing command that you suggested me on Linux machine I can't ping even 172.18.110.1 from vlan!
 
Thanks for helping me!
 
PS I wouldn't use natting for do this

---

### Post by SeijiSensei on 2010-10-12
Sorry, I don't do Windows.  Perhaps you'd be better served to ask on a Windows forum rather than here?

---

### Post by giannir on 2010-10-13
I don't think so because I am working with unix like system and this is a forum about this! If you read well I asked a solution for routing with my ubuntu machine avoiding routings with clients with windows so.
 
Thanks

---

### Post by robertrose6 on 2010-10-13
Are you trying to get the windows box to act as a router?
From what I have been told you need a router to talk between Vlans.

---

### Post by giannir on 2010-10-15
No, I have ubuntu server that routing vlan through shorewall and I works great!
 
I am studing routing and so I would know why I can't route with static rules.

---

