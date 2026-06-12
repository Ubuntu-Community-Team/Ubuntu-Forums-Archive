---
title: "Making a school network"
date: 2013-03-06
forum: Networking &amp; Wireless
---

### Post by morphyrichards1 on 2013-03-06
Hi,
I am trying to create a network to replace the RM Windows network  in my  ICT department as it is not fit for purpose as far as teaching   computer science is concerned.

I'm trying to set the network up as follows...

I will have a server (with Edubuntu on), lets call it "VLE" (it has 2 network interfaces) in my office which will act as:
[LIST]
[*] internet gateway (to internet provided through standard school network via eth0)
[*]Single sign on server / file server etc. so all login authentication and files are stored on this machine
[/LIST]
There  will be a single Cat 6 bus link via eth1 to a switch and in  turn a  server (lets call it "Fred" for now) in a classroom. That has  Edubuntu  also and LTSP.
Fred has a number of (currently 1 for testing) Raspberry Pi computers  running Berryterminal connected in a gigabit ethernet star ...
Students can log into Fred but get their files etc from VLE.
In due course I will add a second classroom with a second server ("Bernie"?). 

I  have to have a single cat 6 cable linking VLE in office to Fred in  room  1 to Bernie in room 2 because I can only get away with a small  amount  of drilling, cant use the existing RM network and can only  afford a smallish amount of kit.

I want each classroom to have it's own application server because I can  make a faster network topology in each room, I believe this will be  better for serving x-graphics whereas internet and file access should  (hopefully) be fine when shared across a single cat 6 link. Also, each  room could have 30 users at a time. For my purposes it would be easier  to make 3 (there are 3 rooms in total) smaller scale applications  servers than one big ultra powerful one that can handle 90 clients at  once.

So, to cut to the chase I'm having a few snags.

So far I've successfully connected to an edubuntu server with a berryterminal. That's easy.
However, I've tried to set up VLE as an internet gateway. Remember it's  connected to my own network via eth1 and to the school internet via  eth0.

I used 'network manager' on VLE to make "Wired connection 2" on eth1 "shared to other computers" via 'method'

On Fred I have added gateway 192.168.0.254 to /etc/network/interfaces and restarted.

ip route show | grep default | awk '{print $3}'
returns
192.168.0.254


However, I still dont seem to be able to share the internet from VLE as a  gateway. (I havent even tried to get started on the difficult stuff yet  either!)

Where am I going wrong?

Many thanks

---

### Post by garcianc2003 on 2013-03-11
Sorry if I am not understanding. Let me see if I get your setup:

[[FRED]]-------[room1_switch]-------||-------[office_switch]-------[[VLE]]------{{Internet}}

I left room 2 out of it for now.

Can you ping across your entire LAN (i.e. from FRED to VLE's eth0 and eth1)?

---

### Post by morphyrichards1 on 2013-03-12
> **garcianc2003 said:**
> Sorry if I am not understanding. Let me see if I get your setup:[[FRED]]-------[room1_switch]-------||-------[office_switch]-------[[VLE]]------{{Internet}}Yes, thats it!> **garcianc2003 said:**
> Can you ping across your entire LAN (i.e. from FRED to VLE's eth0 and eth1)?I can ping across from Fred to VLE across my own network, I'm not sure how to specifically ping eth0 or eth1. I hadn't realised I could do that.I've got three main issues.1) Time is scarce.2) I cant work out why I cant share internet from eth0 to the network on eth1.3) It seems to be quite difficult to set up a single sign on and single home-directory mechanism to work across the department. Today I spent quite a lot of time trying to configure open LDAP to allow this. Seemed to be getting close but kept running into various errors.I've come across this [https://wiki.ubuntu.com/Edubuntu/Specifications/NetworkAuthServer](https://wiki.ubuntu.com/Edubuntu/Specifications/NetworkAuthServer) (but I cant find any more details about it) and it led me to this [http://edsadmin.sourceforge.net/](http://edsadmin.sourceforge.net/) which also looks interesting. I haven't tried this yet.

---

### Post by SeijiSensei on 2013-03-13
VLE needs to masquerade the traffic from the machines behind it to the school network.  To do that, you must first enable the "net.ipv4.ip_forward=1" directive in /etc/sysctl.conf to permit forwarding of packets between interfaces.  By default forwarding is disabled.  Then you need to add an iptables rule to enable masquerading.  If VLE has no other iptables firewalling rules established, then I suggest you add this line to /etc/rc.local:

```
/sbin/iptables -t nat -A POSTROUTING -o eth0 --j SNAT --to-source ip.of.VLE.eth0
```

Replace "ip.of.VLE.eth0" with the IP address assigned to eth0.

---

### Post by morphyrichards1 on 2013-03-13
Thanks for that.
I made those changes but "Fred" still cant access the internet.
The ip addr on eth1 "VLE" (from ip addr show) is 192.168.0.254/24
If I type the same command on Fred I get the same ip address (192.168.0.254/24) for eth0 (it's one and only NW interface)
Is that supposed to happen?

---

### Post by SeijiSensei on 2013-03-13
The Internet facing interface that is connected to the school network should have a address in the same network subnet as the rest of the school.  The network behind VLE should use an entirely different subnet.

Suppose the school network is on 10.10.10.0/24.  Then eth0 on VLE should have an address like 10.10.10.37 with a default gateway that points to the router for 10.10.10.0/24, say 10.10.10.1.  Since VLE's eth1 interface is 192.168.0.254, all the machines that connect to that interface like Fred should have 192.168.0.254 as their default gateway.  That means they hand Internet-bound traffic to VLE's eth1 interface for further routing, then VLE masquerades that traffic as coming from its eth0 interface and passes it upstream to the router for that network.

---

### Post by morphyrichards1 on 2013-03-13
Scratch what I said earlier. Neither machine can see the other across the network. The lights on the switch are on which indicates there is a connection but I cant ping one machine across the network.
Also I can connect with "berry terminal" on a raspi to Fred on the network but not to VLE. (both are LTSP servers)

I currently have got something like this:

Fred-------------------(switch)--------------------------------------------------------------(switch)--VLE
berryterminal------+

---

### Post by morphyrichards1 on 2013-03-13
> **SeijiSensei said:**
> The Internet facing interface that is connected to the school network should have a address in the same network subnet as the rest of the school.  The network behind VLE should use an entirely different subnet.

I've got that - as you say school uses 10.x.x.x. whereas I am using 192.168.x.x

> **SeijiSensei said:**
> Suppose the school network is on 10.10.10.0/24.  Then eth0 on VLE should have an address like 10.10.10.37 with a default gateway that points to the router for 10.10.10.0/24, say 10.10.10.1.  Since VLE's eth1 interface is 192.168.0.254, all the machines that connect to that interface like Fred should have 192.168.0.254 as their default gateway.  That means they hand Internet-bound traffic to VLE's eth1 interface for further routing, then VLE masquerades that traffic as coming from its eth0 interface and passes it upstream to the router for that network.

I will read this more carefully later when I have time and check my understanding. In the meantime, thanks!

---

### Post by morphyrichards1 on 2013-03-14
Clearly I have some learning to do - being vaguely aware of subnets and what they are is one thing. Being able to make a network is entirely different.
Currently I am logging in directly to Fred and to VLE.
Fred has:
```
auto eth0
 iface eth0 inet dhcp
```
in /etc/network/interfaces

VLE has
```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
  address 192.168.0.254
  netmask 255.255.255.0
  dns-search google.com
  dns-nameservers dnsserverip
```

So IP address of eth0 on Fred is showing up as
192.168.1.107/24

eth1 on VLE is 192.168.0.254/24

Pinging one from the other results in 100% packet loss.

The two are connected via a single cat6 link and switches on either end

[Fred]--(switch)----...---(switch)--[VLE]

The relevant lights are on which indicates to me that the physical connection is sound.

Two more questions...
1) Why does this most basic of things not work?
2) Is there a specifically made for Ubuntu networking for dummies step by step tutorial that anyone can recommend? (not "here let me google that for you" ;))

---

### Post by SeijiSensei on 2013-03-14
> **morphyrichards1 said:**
> 
VLE has
```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
  address 192.168.0.254
  netmask 255.255.255.0
  dns-search google.com
  dns-nameservers dnsserverip
```


There's no specification for eth0 on VLE?  Then it has no address.  Is it supposed to be getting an address from a DHCP server on the school network?  If so, then add a stanza to /etc/network/interfaces on VLE like the one on Fred:
```

auto eth0 
iface eth0 inet dhcp

```

> 
So IP address of eth0 on Fred is showing up as
192.168.1.107/24

eth1 on VLE is 192.168.0.254/24

Pinging one from the other results in 100% packet loss.

They are not in the same subnet.  You can only exchange packets between 192.168.0.0/24 and 192.168.1.0/24 if there is a router between them.  

Perhaps a good book might help, like maybe [http://shop.oreilly.com/product/9780596102487.do](http://shop.oreilly.com/product/9780596102487.do).  There's also the [Linux Network Administrator's Guide](http://www.tldp.org/LDP/nag2/index.html).

---

### Post by morphyrichards1 on 2013-03-14
Adding this to interfaces on Fred
```


auto eth0 
iface eth0 inet static   
address 192.168.0.250   
netmask 255.255.255.0   

```
In an attempt to put both machines in the same subnet now gives me "host unreachable" - which seems to be a vast improvement to previous(nothing at all)

Have some time this evening so will do some reading. Many thanks for your help so far :)

---

### Post by morphyrichards1 on 2013-03-14
In an attempt to put both machines in the same subnet I tried
```

auto eth0
iface eth0 inet static
address 192.168.0.250
netmask 255.255.255.0

```
Pinging VLE from Fred now gives the response
response from 192.168.0.254 destination host unreachable
Which seems to be a vast improvement.

Have some time this eveing so I will do some reading.
Thanks for your help so far :)

---

### Post by morphyrichards1 on 2013-03-14
[COLOR=#444444][FONT=Calibri]VLE[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]ip 192.168.0.254[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sn 255.255.255.0[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Class C Natural mask = 255.255.255.0[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]So, if I am using this. The subnet is a logical AND between ip and subnet mask[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]VLE[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]ip   11000000.10101000.00000000.11111110 = 192.168.0.254[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sm 11111111.11111111.11111111.11110000[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sn  11000000.10101000.00000000.11110000 = 192.168.0.240[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Fred[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]ip 192.168.0.250[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sn 255.255.255.0[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]ip   11000000.10101000.00000000.11111010 = 192.168.0.250[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sm 11111111.11111111.11111111.11110000[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sn  11000000.10101000.00000000.11110000 = 192.168.0.240[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]So these two machines are in the same subnet?[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]So, ping should work? Cant test this until I get back to work but I will investigate why destination host is unreachable and ask further questions later ...[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Anyway, planning things further, I am going to have .. lets call them zones. I am going to have 6 zones (I think)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]VLE Zone[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]This is a proper enterprise server, will be LDAP / Kerberus / internet gateway / email and moodle server to my computing network on eth1 and moodle server to the school network on eth0.[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Fred Zone[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Purely experimental LTSP server on an ancient PC while I try to get my head around what's going on...[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Lovelace Zone[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Doesnt exist yet, will be an LTSP server built on a reasonably high spec computer in a classroom for berry terminals and 'gateway'(?) for a few Edubuntu PC's for occasions where a r-pi based thin client is not enough (such as video editing)[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Emeagwali Zone[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]As above[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Turing Zone[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]As above[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Berners-Lee zone[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Wont exist for some time but will eventually become another network. As above except an unused network is already in existence here.[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]So, I will need to create 6 subnets?[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Anyway ...[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Can I configure my subnet mask to allow up to eight subnets by using the subnet mask 255.255.255.224 instead of 255.255.255.0?[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]11111111.11111111.11111111.11100000 is /27 bits set with each subnet having 32 host addresses / 30 use-able. There are 30 work places in a classroom.[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]VLE[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]ip   11000000.10101000.00000000.11111110 = 192.168.0.254[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sm 11111111.11111111.11111111.11100000[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sn  11000000.10101000.00000000.11111100 = 192.168.0.252[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Fred[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]ip   11000000.10101000.00000000.11111010 = 192.168.0.250[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sm 11111111.11111111.11111111.11100000[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]sn  11000000.10101000.00000000.11100000 = 192.168.0.224[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Hmmm, different subnets. Where to from here?[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Does this mean I will need routers rather than switches between each room / zone? What would be a suitable router, all my searches yield ADSL etc routers which I don't think I am after.[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]Most "machines" will be r-pi berryterminals. Do they count? (ie. does a thin client have an independent ip address?) Can I have 30 berryterminals, 5 or 6 PC's and a few more R-Pi's running their native Raspbian that students can use to make small scale web-servers, wifi robots etc?[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#444444][FONT=Calibri]My brain is beginning to ache a little bit. Time for beer and food.[/FONT][/COLOR]

---

### Post by morphyrichards1 on 2013-03-14
Hmmm ... To access it's own subnet and the wider network, each server (Fred, Lovelace, et al) also needs 2 network interfaces? Then it's also able to act as a router? And I need to get my head around iptables too.Is there anything else?(I need to buy the Linux Networking Cookbook)

---

