---
title: "unable to share Internet over ethernet cable"
date: 2013-01-30
forum: Networking &amp; Wireless
---

### Post by dbclinton on 2013-01-30
I used the Network Manager GUI to set the client-facing interface on my server to "shared to other computers" and I'm able to ping back and forth between my server and the client (the client is getting its IP address from the server's DHCP), but I have no Internet connectivity on the client. 
I know it's not just a DNS problem, because, besides being unable to resolve domain names, I also can't ping Internet sites by IP addresses.
Does anyone have any ideas?
Thanks,
David

---

### Post by sanderj on 2013-01-30
On the client, what does

```
ip route show

```
show?

---

### Post by dbclinton on 2013-01-30
ip route show output:
> default via 192.168.0.1 dev eth0 proto static
192.168.0.0/24 dev eth0 proto kernal scope link src 192.168.0.28 metric 1

192.168.x.x is my server's domain.
Thanks,

---

### Post by sanderj on 2013-01-30
> **dbclinton said:**
> ip route show output:


192.168.x.x is my server's domain.
Thanks,

And what's x.x? You can tell because those are private addresses; useless outside of your LAN so useless for hackers.

---

### Post by dbclinton on 2013-01-30
Sorry.
My server is 192.168.0.254
I should add that my server is getting Internet from a router using 10.0.0.2
Here's my server's ip route show:

> 10.0.0.0/24 dev eth2  proto kernel  scope link  src 10.0.0.2  metric 1 
10.0.3.0/24 dev lxcbr0  proto kernel  scope link  src 10.0.3.1 
169.254.0.0/16 dev eth1  scope link  metric 1000 
192.168.0.0/24 dev eth1  proto kernel  scope link  src 192.168.0.254

---

### Post by sanderj on 2013-01-30
> **dbclinton said:**
> Sorry.
My server is 192.168.0.254
I should add that my server is getting Internet from a router using 10.0.0.2
Here's my server's ip route show:

So "default via 192.168.0.1 " but your server sharing Internet is on "192.168.0.254". That makes completely clear why it doesn't work: your client sends all Internet traffic to 192.168.0.1, but it should go to 192.168.0.254.

---

### Post by Tony Flury on 2013-01-30
A 10.x.x.x address is also a private address - so also useless for the internet. So either you must have a public address somewhere, or your connections at being NAT'd by your ISP.

Either way though it shouldn't make a difference.

what happens when you do a traceroute to a known good public IP address ?

---

### Post by dbclinton on 2013-01-30
> So "default via 192.168.0.1 " but your server sharing Internet is on "192.168.0.254". That makes completely clear why it doesn't work: your client sends all Internet traffic to 192.168.0.1, but it should go to 192.168.0.254.

Should I manually add the address 192.168.0.254 on the client's Network Manager under IPv4 settings?

---

### Post by furything on 2013-01-30
Please can you 
```
ifconfig
```
on your server?

Just want to make sure things are set up as you think they are.

The default for share to other computers via network manager for 12x and it might have been 11x ubuntu is 10.42.0.X
On older systems it was 10.40.0.x

---

### Post by dbclinton on 2013-01-30
ifconfig:
> eth0      Link encap:Ethernet  HWaddr 00:1d:60:0b:41:e5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:87:11:0a:03:31  
          inet addr:192.168.0.254  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::287:11ff:fe0a:331/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:840 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51348 (51.3 KB)  TX bytes:9877 (9.8 KB)
          Interrupt:22 Base address:0xac00 

eth2      Link encap:Ethernet  HWaddr 00:a1:b0:00:5b:ce  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2a1:b0ff:fe00:5bce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11789 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12321 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8674016 (8.6 MB)  TX bytes:2080656 (2.0 MB)
          Interrupt:23 Base address:0xb400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:196509 (196.5 KB)  TX bytes:196509 (196.5 KB)

lxcbr0    Link encap:Ethernet  HWaddr 06:d3:f3:a5:12:03  
          inet addr:10.0.3.1  Bcast:10.0.3.255  Mask:255.255.255.0
          inet6 addr: fe80::4d3:f3ff:fea5:1203/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:19099 (19.0 KB)

Thanks,

---

### Post by sanderj on 2013-01-30
> **dbclinton said:**
> Should I manually add the address 192.168.0.254 on the client's Network Manager under IPv4 settings?

Preferrably NOT. The default gateway is set via DHCP (right?), so correct it via DHCP ...

---

### Post by furything on 2013-01-30
Ok what is your firewall rule set? What is in the iptables?

The network manager sets some things up by default and I know mine were wrong.

---

### Post by dbclinton on 2013-01-30
> Preferrably NOT. The default gateway is set via DHCP (right?), so correct it via DHCP ...
Ok, so I used 
> route add default gw 192.168.0.254
to add a new gateway on my client (and I used del to remove the old one).
> route -n 
now gives me something like: 
> Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 eth0
198.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

But I'm still getting no Internet. And besides that, my gateway settings are not persistant over boots...

---

### Post by dbclinton on 2013-01-30
> Ok what is your firewall rule set? What is in the iptables?
Here's iptables -L from the host machine:
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
Nanny      all  --  anywhere             anywhere            

Chain Nanny (1 references)
target     prot opt source               destination

And there's nothing more on the client (since I haven't got internet access from the client, I can't install sshd to actually go in there and copy the text :))
Thanks

---

### Post by furything on 2013-01-30
please can you also check/post
```
 iptables -t nat -L -v
```

Will be offline for awhile as about to go home. Will take a look at result later nad try and string something together appropriate to your set up

---

### Post by dbclinton on 2013-01-30
Here is iptables -t nat -L -v from my server:

> Chain PREROUTING (policy ACCEPT 12 packets, 1311 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 10 packets, 882 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 482 packets, 30101 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 479 packets, 29713 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    3   388 MASQUERADE  all  --  any    any     10.0.3.0/24         !10.0.3.0/24

My client's iptables included those four Chains with policy:ACCEPT but with 0 packets and bytes and no Masquerade output line.

---

### Post by furything on 2013-01-30
Ok you need to set up port forwarding
 see [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

so if I have you eth ports correctly
eth1 internal 192.168.0.x
eth2 external 10.0.0.x
flush tables first (in code)
```
sudo iptables -t nat -F
sudo iptables -F
sudo iptables -A FORWARD -o eth1 -i eth2 -s 10.0.0.0/24 -m conntrack --ctstate NEW -j ACCEPT 
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT 
sudo iptables -t nat -F POSTROUTING 
sudo iptables -t nat -A POSTROUTING -o eth2 -j MASQUERADE
```also  edit /etc/sysctl.conf and uncomment: 
#net.ipv4.ip_forward=1... so that it reads: 
net.ipv4.ip_forward=1

from http link above 
Read the link fully to make sure nothing is missed. If your internet starts to work then use the link to see how to make these changes persist. (I do it differently so if you get a problem I will tell you my way)

NOTE this is not the same for using a proxy server like squid3 although from memory it sort of works. If using Squid Dansguardian the tables need to be different

---

### Post by dbclinton on 2013-01-30
> Ok you need to set up port forwarding

Well that did it! I have Internet access on my client. Now if only I could figure out how to make the client's gateway settings persistant...
Thanks a million!
David

---

### Post by furything on 2013-01-31
>  Now if only I could figure out how to make the client's gateway settings persistant...

The client does not need a anything in the iptables to talk to the server. You can have some fire wall to protect it though.

If your local network is shared out as dchp from the server then the client should be set to automatic (dhcp) and it should request the ip from the server.

However on the client you can set manually (even if there is a dhcp). This asks for ip of client network mask 255.x.x.x and gateway. Normally mask of 255.255.255.0 if local network (MUST be same as server mask and depends on number of computers you want to attach).

---

### Post by dbclinton on 2013-01-31
>  If your local network is shared out as dchp from the server then the client should be set to automatic (dhcp) and it should request the ip from the server.
For some reason my client's gateway setting keeps reverting to 192.168.0.1 (from the 192.168.0.254 I'd set it to using ip route add default).
Now my server, on the other hand, didn't keep its iptables settings despite my linking to /etc/iptables.sav from rc.local. Apparently, my system isn't reading rc.local at boot.

---

