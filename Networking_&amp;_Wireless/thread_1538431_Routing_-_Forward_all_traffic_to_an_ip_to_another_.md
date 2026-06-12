---
title: "Routing - Forward all traffic to an ip to another ip"
date: 2010-07-25
forum: Networking &amp; Wireless
---

### Post by bsgcic on 2010-07-25
I need to be able to do the following:

Physical Router located at 192.168.40.1

On Ubuntu 10.04 Lucid machine:
eth0 with static ip 192.168.40.2
eth1 with static ip 192.168.40.3
eth2 with static ip 192.168.40.4

Associate a virtual address to eth1 with an entirely different network address such as 192.168.50.1
Do the same (virtual address) for eth2 -- e.g. 192.168.60.1

In the application:
register phone number A at 192.168.40.1  (The application will automatically use eth0 for this)
register phone number B at 192.168.50.1
register phone number C at 192.168.60.1

Somehow forward all traffic (including the register request) sent to 192.168.50.1 to 192.168.40.1 as if the register had been made directly to 192.168.40.1. In other words, the app "sends" registration and traffic to 192.168.50.1 but then Ubuntu forwards it to 192.168.40.1 (but the app does not know that).

Similarly, forward all traffic sent to 192.168.60.1 to the router at 192.168.40.1.

Do the same for the reverse, forward all traffic that the router sends back to 192.168.40.3 (eth1) to 192.168.50.1 (within the Ubuntu machine) so that the app knows it is for phone B.
Similarly forward all traffic that the router sends back to 192.168.40.4 (eth2) to 192.168.60.1 so that the app knows it is for phone C.

Thus, the application believes that it is registering at 3 completely separate routers on 3 completely separate networks via 3 separate network interfaces but in fact is really registering all three to the same router (but does not know that).

Similarly, the router believes that it is receiving 3 separate registrations because it receives each registration request and traffic from 3 separate interfaces and thus 3 separate mac addresses (i.e., of eth0, eth1, and eth2).

Traffic sent to and from the router for each of the 3 phone numbers (via eth0, eth1, and eth2) are not mixed because the translation happens in both directions.

I have been searching via google, looking into iptables, brctl, ipfwadm, etc and am lost.
Your help would be greatly appreciated.

Thanks

---

### Post by HermanAB on 2010-07-25
Read up on the iptables redirect command.  You could also use socat.

---

### Post by bsgcic on 2010-07-25
Herman,

Thank you very much for your help.

I have been reading up on both iptables redirect and on socat. I am quite overwhelmed by both.

I have tried the following with no luck:

ifconfig eth2:1 192.168.50.1 netmask 255.255.255.255
iptables -t nat -A PREROUTING -d 192.168.50.1 -j DNAT --to-destination 192.168.40.1

But it did not work. I could ping 192.168.50.1 before and after I executed the iptables command but it apparently is still not redirecting to the router because the registration to 192.168.50.1 is unsuccessful.

Could you post a command either iptables or socat?

Thanks

---

### Post by YesWeCan on 2010-07-25
Hi. I don't think I can help. But I am interested in understanding what it is you are trying to do. :)

Suppose you actually had 3 routers. You would then have three subnets:
192.168.40.0/24  gw 192.168.40.1
192.168.50.0/24  gw 192.168.50.1
192.168.60.0/24  gw 192.168.60.1

What you appear to want to do is have your server pretend that it has connections to these 3 subnets even though it only has a single subnet and single gateway.

Is that right?

---

### Post by bsgcic on 2010-07-25
Yes, I believe that is the terminology for what is needed. The app (Asterisk) needs to think it is registering to a separate subnet; otherwise it will just use eth0 for everything and the router will deny the registrations.

---

### Post by kipioca on 2010-07-27
Hi,

have you tried :
iptables -t nat -A PREROUTING -d 192.168.50.1 -j DNAT --to-destination 192.168.40.1
iptables -t nat -A POSTROUTING -j MASQUERADE

In the case it works, you must know that you can chain PREROUTING rules Ex:

iptables -t nat -A PREROUTING -d 192.168.50.2 -j DNAT --to-destination 192.168.40.2
iptables -t nat -A PREROUTING -d 192.168.50.1 -j DNAT --to-destination 192.168.40.1
iptables -t nat -A POSTROUTING -j MASQUERADE

---

### Post by YesWeCan on 2010-07-27
This may be completely crazy and show up my lack of understanding of networking but what if you used one NIC as the client and another NIC as a fake router?
Consider a simplified case for illustration. You set one NIC (eth1) with IP 192.168.60.2 (the "client") and you set another NIC (eth2) with IP 192.168.60.1 (the "router"). You set iptables so anything received from eth2 is SNAT'ed to the real router at 192.168.40.1 via eth0. You physically connect the LAN cards together. I reckon this would fool your app. into thinking there is a real .60 subnet and a real .60.1 router.
If this proposal is valid then you could duplicate the pairs of NICs for each phone number. However, I think you may be able to use only 3 NICs if you set the fake router IPs up as aliases of the "client" NICs. So long as the app doesn't notice that one client and one router share the same MAC address it may be none the wiser.

---

### Post by bsgcic on 2010-07-28
I nearly got it working but still no dice.
 
iptables -t nat -A OUTPUT -p all -d 192.168.40.3 -j DNAT --to-destination 192.168.40.1
(Note: -A PREROUTING did not work at all but -A OUTPUT got me closer)
iptables -t nat -A POSTROUTING -p all -j MASQUERADE
iptables -t nat -n -L
Chain PREROUTING (policy ACCEPT)
target prot opt source destination 
 
Chain POSTROUTING (policy ACCEPT)
target prot opt source destination 
MASQUERADE all -- 0.0.0.0/0 0.0.0.0/0 
 
Chain OUTPUT (policy ACCEPT)
target prot opt source destination 
DNAT all -- 0.0.0.0/0 192.168.40.3 to:192.168.40.1 
 
"ping 192.168.40.3 -I eth1" and "ping 192.168.40.3" both work fine.
I can access the router and login to it via [http://192.168.40.3/](http://192.168.40.3/). Therefore port 80 is working.
 
route -n
Receipt Site Gateway Netmask Flags Metric Ref Use # Interface
192.168.40.1 0.0.0.0 255.255.255.255 UH 0 0 0 eth0
0.0.0.0 192.168.40.1 0.0.0.0 UG 0 0 0 eth0
 
ip route show
192.168.40.1 dev eth0 proto static scope link 
default via 192.168.40.1 dev eth0 proto static 
 
ip rule show
0: from all lookup local 
32766: from all lookup main 
32767: from all lookup default 
 
 
ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
inet 127.0.0.1/8 scope host lo
etc....
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
inet 192.168.40.2/32 brd 192.168.40.2 scope global eth0
etc....
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
inet 192.168.40.3/32 brd 192.168.40.3 scope global eth1
etc....
5: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
etc....
(eth2 is currently down)
 
 
In Asterisk 1.4.33.1, sip.conf
bindport=5060
bindaddr=0.0.0.0
rt200ne=192.168.40.1
rt200ne=192.168.40.3
 
register => 3:username:password@192.168.40.1/123456789
will register but
register => 3:username:password@192.168.40.3/123456789
will not register
 
Any ideas why ping and http to 192.168.40.3 is successfully directed to 192.168.40.1 but the asterisk registration to 192.168.40.3 on port 5060 is not? Any ideas as to things to try to fix this?
 
YesWeCan - Interesting. What do you mean by "physically connect the LAN cards together"?
 
Thanks!!

---

### Post by YesWeCan on 2010-07-28
I mean actually use LAN cables and a switch to connect the NICs. My idea is to simulate having 2 PCs and a router: Asterix runs on PC-A which has eth1=192.168.60.2 connected to PC-B eth2=192.168.60.1. PC-B also has eth0=192.168.40.2 connected to the router=192.168.40.1. Instead of having 2 PCs you fold PC-B into PC-A, so that PC-A has all 3 NICs and eth1 & eth2 are wired together and eth0 is wired to the router.


With regard to trying to do this using iptables alone, I need to understand exactly what Asterix is expecting. I do not understand what Asterix does when it "registers". What does it need to see in terms of IP and MAC addresses? What does the router need to see. Eg: do the packets arriving at the router need to have source=192.168.60.2 etc or is it ok for the router to see everything as source=192.168.40.2?

About iptables. I believe PREROUTING, INPUT and FORWARD functions only apply to packets originating from a NIC. Packets that are forwarded bypass the kernel/local switchboard and go straight to postrouting. Asterix packets presumably originate at the kernel switchboard and therefore will only get affected by the OUTPUT and POSTROUTING functions on their way to a NIC. This is probably why your prerouting rule didn't work.

---

### Post by YesWeCan on 2010-07-28
ignore

---

### Post by bsgcic on 2010-07-29
The router restricts registrations by mac address /ip of the nic. Thus, the router needs to receive the registrations from separate nics. Do you think that would be the case with the PC-A PC-B setup?

Asterisk does not place an restrictions but needs to know to send call traffic to through the nic used to register each phone. Unfortunately it does not support binding trunks to interfaces. Asterisk needs to do something with the rt200ne= statement for authentication I think as well as each register statement.

It is strange that I can access, log into, and configure the router via  firefox to 192.168.40.3 but asterisk cannot register via
rt200ne=192.168.40.3
register => 3:usernameassword@192.168.40.3/phonenumber2
 
I have also been looking for packages and other programs that I could install on the box that might help. Haven't found any and thus really stuck.

---

### Post by YesWeCan on 2010-07-29
I am guessing here but maybe I can spark some ideas. If your router checks the NIC MAC address then using eth0 for all registrations may not work and MASQUERADE definitely won't work because the router will see the same source IP each time. So my previous idea would not work either.

I am not sure whether you can fake the MAC address of a NIC.

What if you use a wide subnet for the NICs and router, say 192.168.0.0/16? Then you could set the IP address of eth0=192.168.40.2, eth1=192.168.50.2, eth1=192.168.60.2. Set the gateway of each NIC to be the router IP=192.168.40.1.
Would this allow you to talk to the router directly via each NIC and the router would see a different MAC and source IP for each registration. This may or may not work for Asterix depending on how it defines a subnet, ie: does it assume the network is class C and distinguish the subnets by the 3rd IP octet?

---

### Post by bsgcic on 2010-07-29
A wide subnet is interesting. I am guessing that asterisk does not care whether it is class C / distinguish by the 3rd octet. But I am not really sure.
I would still need to have each registration statement register to a "different" destination to force them to use each's nic. Not sure how that would work.
Somehow:
rt200ne=192.168.40.1
rt200ne=192.168.50.1
rt200ne=192.168.60.1
 
register => 3:username:password@192.168.40.1/phonenumber1
register => 4:username:password@192.168.50.1/phonenumber2
register => 5:username:password@192.168.60.1/phonenumber3
 
where 192.168.50.1 and 192.168.60.1 both ultimately go to the router at 192.168.40.1 via the separate nics.

Also, there is a separate unrelated internal network at 192.168.175.0
Would widening the internet access router from 192.168.40.0 to 192.168.0.0 put the internal 192.168.175.0 lan at greater risk of unauthorized access from the wan or other attack from the internet?

Thanks!!

---

### Post by YesWeCan on 2010-07-29
Yes, you would probably need to use DNATs to map each NIC gw to the router address.
I suppose you can always set up a postrouting rule to drop any packets with destination 192.168.175.0/24.
The iptables man page is a challenge to me but it appears that a natty surveillance feature is to log packets before you drop them, like:

POSTROUTING -d 192.168.175.0/24 -j LOG --log-level X --log-uid
POSTROUTING -d 192.168.175.0/24 -j DROP

---

### Post by bsgcic on 2010-07-29
Thanks. I'll try that out.

---

### Post by infant_coder on 2011-06-23
Hi,

I have got three PC's connected to a router. 

PC1 and PC2 are connected to wireless interface -ath0. 
Router's ath0 :192.168.12.1
PC1: 192.168.12.2
PC2: 192.168.12.3

PC3 is connected to eth0 of Router.
Router's eth0 :192.168.14.1
PC3 : 192.168.14.2

I am pinging PC1 --> PC3
Is it possible to forward icmp packets from PC3 to PC2   ? 

Command executed on router:
iptables -t nat -A PREROUTING -p icmp -d 192.168.14.2 -j DNAT --to-destination 192.168.12.3

Pls verify the command.

---

