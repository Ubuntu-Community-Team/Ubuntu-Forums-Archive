---
title: "iproute2 and iptables"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by CyberPingU on 2011-08-02
Hello all,
I have two connections on my linuxbox, that are eth0 and usb0, both working.
I would like to set a routing rule so
- when I want to connect to a site on port 80 and 443, connection must route through eth0;
- in other cases I want it to route through usb0.

What I did is:

```

# iptables -A OUTPUT -t mangle -p tcp -m multiport --dports 80,443 -j MARK --set-mark 0x1
# route add default gw 192.168.0.1 // ip address of the gateway on usb0
# echo 201 desire >> /etc/iproute2/rt_tables
# ip rule add fwmark 1 table desire
# ip route add default via 192.168.1.1 dev eth0 table desire // this is the ip of the gateway on eth0
# ip route flush cache

```
Unluckily I can ping, traceroute, ssh and telnet everywhere but I cannot surf the Internet, so the connection on ports 80 and 443 is blocked, and not only routed on the right link...
Any ideas?

---

### Post by Beacon11 on 2011-08-02
After running the commands, can you provide the output of the route command please? Thank you.

---

### Post by CyberPingU on 2011-08-03
Here are outputs:

```

**# ip rule ls**
0:	from all lookup local 
32765:	from all fwmark 0x1 lookup desire 
32766:	from all lookup main 
32767:	from all lookup default1

**# ip route show**
192.168.1.0/24 dev eth1  proto kernel  scope link  src 192.168.1.6 
192.168.42.0/24 dev usb0  proto kernel  scope link  src 192.168.42.230  metric 1 
192.168.122.0/24 dev virbr0  proto kernel  scope link  src 192.168.122.1 
10.2.0.0/16 dev tap0  proto kernel  scope link  src 10.2.0.3 
169.254.0.0/16 dev eth1  scope link  metric 1000 
default via 192.168.1.17 dev eth1  metric 100

**# ip route show table desire**
default via 192.168.42.129 dev usb0

**# iptables -t mangle -L**
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
MARK       tcp  --  anywhere             anywhere            multiport dports www,https MARK set 0x1 

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination




```

As you can see the scenario is a bit different:
- eth1 is the ethernet nic with address 192.168.1.6, its gateway is 192.168.1.17;
- usb0 is the other nic with address 192.168.42.230, its gateway is 192.168.42.230

---

### Post by bighippo999 on 2011-08-03
Hi,

I had to register to reply to this one as I'm just trying to do the same sort of thing and it's not working.

Basically my setup is this
Server A - Has an Ethernet (local Network) and PPP connection (Internet) as well as 3 VPN tunnels to server B, C & D (which go via PPP).
What I'm doing at the moment is setting the default route of Server A into the tunnel going to Server B. Server B then masquarades all traffic that isn't intended for the local networks.

Server A is working as a router, and what I want to do is based on the MAC address of Laptop A forward down to Server C, Laptop B down to Server D and everthing else carries onto Server A.


I have in my ip tables:-

```
root@Tardis:/# iptables -t nat -nvL
Chain PREROUTING (policy ACCEPT 216K packets, 14M bytes)
 pkts bytes target     prot opt in     out     source               destination         
16668 1228K MARK       all  --  *      *       0.0.0.0/0            0.0.0.0/0           MAC 00:1B:77:6E:D6:E3 MARK xset 0x1/0xffffffff 
1668  143K MARK       all  --  *      *       0.0.0.0/0            0.0.0.0/0           MAC F4:6D:04:24:EE:33 /* Transformer */ MARK xset 0x2/0xffffffff 
```

Pretty much the same expect the 2nd entry also has a comment. As you can see by the pkts these rules are being hit.

In the routes then I have:-

```
root@Tardis:/# ip rule list
0:	from all lookup local 
32764:	from all fwmark 0x2 lookup LUKE 
32765:	from all fwmark 0x1 lookup ME
32766:	from all lookup main 
32767:	from all lookup default 

root@Tardis:/# ip route list table 1
default via 192.168.200.204 dev tun200 
root@Tardis:/# ip route list table 2
default via 192.168.205.204 dev tun205 
root@Tardis:/# ip route show
default via 192.168.202.204 dev tun202

```

Now the reason I had to register was this. It doesn't work, however if I add a rule specific for the IP address of Laptop A:-
```
ip rule add from 192.168.204.100 table ME
```

It works just fine, so it looks like I have something wrong between the firewall and the route rules. So I'd suggest trying to add an IP address into the route rule list and see if it works without the firewall involved.

I think I'm still going to need it unless the route rules can work by mac address. But at least it's given me something to work with. Will update again later with anything else I can find out. 

Hope this helps you a little.

---

### Post by bighippo999 on 2011-08-03
Hi Again,

A bit more info. After looking at your example I can see your using the mangle table and not the nat, so I added my rules into mangle into the prerouting. This broke the laptop getting out all together but I could see the rule was being hit the same as before.

So assuming that this was doing something as it's now stopping the traffic but Laptop B is still working I kept searching and come across this [http://www.linuxquestions.org/questions/linux-networking-3/route-eth2-tcp-packets-to-tun0-with-iptables-and-ip-rule-route-879519/](http://www.linuxquestions.org/questions/linux-networking-3/route-eth2-tcp-packets-to-tun0-with-iptables-and-ip-rule-route-879519/)

Basically I need the command
```
echo 2 > /proc/sys/net/ipv4/conf/tun200/rp_filter
```

I prove this by adding the 2nd laptop into the mangle prerouting and because it uses a different tun interface which I haven't run the echo on the traffic just hangs.

I have no idea if any of this will help, but I'd really try adding an IP into the rule set and bypass the firewall, it should at least prove your routing is working and it's down to the firewall.

On a side note: [http://www.whatsmyip.org/](http://www.whatsmyip.org/) really didn't take well to me hitting it quite a bit in testing, which kinda screwed me up for a bit thinking it's not working when in fact the net was, So best to vary.

Cheers,

---

