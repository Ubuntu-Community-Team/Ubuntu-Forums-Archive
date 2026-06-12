---
title: "Getting two network cards to talk to each other"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by MrXpress on 2009-09-17
I'm almost criminally dumb at networking, but this is a problem that needs to be solved.

We have a phone server with two NICs, one that is connected to the main network (192.168.1.xxx, eth0), and the other that is connected to the VoIP phones and is the DHCP server for them (192.168.0.xxx, eth1). eth0 is connected to a router, eth1 goes to a switch which goes to the phones. Everything works as intended with external addresses, I just can't get the two to talk to each other (i.e., ping -I eth0 192.168.0.1 doesn't work, and vice versa). 

The main goal is simply to have the phones on the eth1, 192.168.0.xxx subnet be able to talk to the LDAP server at 192.168.1.100. I've tried searching and the common theme seems to be adding routes, I'm just not sure how exactly to implement that in this case.


A route -n produces this:

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
```

Any help would be much appreciated. Like I said, I'm no wizard at this stuff so I'm sure I'm leaving out vital details and/or missing an obvious solution.

---

### Post by louigi600 on 2009-09-17
home@eng-prova:/etc$ sudo sysctl -a | grep forward
error: "Invalid argument" reading key "fs.binfmt_misc.register"
error: permission denied on key 'net.ipv4.route.flush'
net.ipv4.conf.all.forwarding = 0
net.ipv4.conf.all.mc_forwarding = 0
net.ipv4.conf.default.forwarding = 0
net.ipv4.conf.default.mc_forwarding = 0
net.ipv4.conf.lo.forwarding = 0
net.ipv4.conf.lo.mc_forwarding = 0
net.ipv4.conf.eth0.forwarding = 0
net.ipv4.conf.eth0.mc_forwarding = 0
net.ipv4.conf.wmaster0.forwarding = 0
net.ipv4.conf.wmaster0.mc_forwarding = 0
net.ipv4.conf.wlan0.forwarding = 0
net.ipv4.conf.wlan0.mc_forwarding = 0
net.ipv4.conf.pan0.forwarding = 0
net.ipv4.conf.pan0.mc_forwarding = 0
net.ipv4.ip_forward = 0
net.ipv6.conf.all.forwarding = 0
net.ipv6.conf.default.forwarding = 0
error: permission denied on key 'net.ipv6.route.flush'
net.ipv6.conf.lo.forwarding = 0
net.ipv6.conf.eth0.forwarding = 0
net.ipv6.conf.wmaster0.forwarding = 0
net.ipv6.conf.wlan0.forwarding = 0
net.ipv6.conf.pan0.forwarding = 0
home@eng-prova:/etc$

You can see that my machine also does not forward network traffic between interfaces
You might like to set to 1 these values
net.ipv4.conf.all.forwarding
net.ipv6.conf.all.forwarding

by altering the content of /etc/sysctl.conf you can make your changes permanent across reboots.
To load your altered sysctl.conf do
```
sudo sysctl -p
```

---

### Post by MrXpress on 2009-09-17
The ipv4/ipv6 forwarding is enabled. What perplexes me is that the only way the computers on the eth1 subnet are getting the internet is through eth0, because that's the only link from the server to the router (and indeed, a traceroute to, say, google.com has the router (192.168.1.1) show up as the second hop .. yet a traceroute to 192.168.1.101 stalls out at that same second hop that succeeded before).

---

### Post by louigi600 on 2009-09-17
Do you have iptables configured on the 2 nic machine ?
If so show me the output of "iptables-save" (if you do not know that is not a typo it's a single word).

---

### Post by MrXpress on 2009-09-17
> **louigi600 said:**
> Do you have iptables configured on the 2 nic machine ?
If so show me the output of "iptables-save" (if you do not know that is not a typo it's a single word).

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
DROP       all  --  anywhere             192.168.1.0/24      
ACCEPT     all  --  192.168.1.0/24       anywhere            
ACCEPT     all  --  anywhere             192.168.1.0/24      

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

This is how we have it set up currently. I was reading about changing something with masquerade, but I'm unsure if that would resolve the situation or not.

---

### Post by louigi600 on 2009-09-17
That's the output of "iptables -nL" .... and only has the filter tables.
I wanted "iptables-save" to get a veiw of all the config including nat ....

Anyway I thing your filter tables are wierd ...
The only thing that you are dropping are packets that are routed trough the 2 nik machine and whose destination is 192.168.1.0/24
You then have another entry stating the exact opposite ... whatever you intended I doubt that what you showed me is what you want.

---

### Post by MrXpress on 2009-09-17
> **louigi600 said:**
> That's the output of "iptables -nL" .... and only has the filter tables.
I wanted "iptables-save" to get a veiw of all the config including nat ....

Anyway I thing your filter tables are wierd ...
The only thing that you are dropping are packets that are routed trough the 2 nik machine and whose destination is 192.168.1.0/24
You then have another entry stating the exact opposite ... whatever you intended I doubt that what you showed me is what you want.

```
# Generated by iptables-save v1.4.1.1 on Thu Sep 17 14:11:27 2009
*nat
:PREROUTING ACCEPT [27:2400]
:POSTROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [1:57]
-A POSTROUTING -o eth0 -j MASQUERADE 
COMMIT
# Completed on Thu Sep 17 14:11:27 2009
# Generated by iptables-save v1.4.1.1 on Thu Sep 17 14:11:27 2009
*filter
:INPUT ACCEPT [95:7958]
:FORWARD ACCEPT [5:625]
:OUTPUT ACCEPT [64:8006]
-A FORWARD -d 192.168.1.0/24 -i eth1 -j DROP 
-A FORWARD -s 192.168.1.0/24 -i eth1 -j ACCEPT 
-A FORWARD -d 192.168.1.0/24 -i eth0 -j ACCEPT 
COMMIT
# Completed on Thu Sep 17 14:11:27 2009
```

---

### Post by louigi600 on 2009-09-17
Ok all the stuff going out of eth0 gets masqueraded ... you might not want to do this if you want the 2 networks to inter-operate.
That single rule might have to be changed to a more complicated one or become more then one rule.
The easiest way is probably to make it 2:
-A POSTROUTING -i eth1 -o eth0 -d ! 192.168.0.0/24 -j MASQUERADE
-A POSTROUTING -i eth0 -o eth0 -d ! 192.168.1.0/24 -j MASQUERADE

Also your filter rules need review since POLICY is ACCEPT you might as well remove these 2:
-A FORWARD -s 192.168.1.0/24 -i eth1 -j ACCEPT 
-A FORWARD -d 192.168.1.0/24 -i eth0 -j ACCEPT

The rest means that anything coming from eth1 and destination to 192.168.1.0/24 is dropped. As far as I understand this means that anything coming from 192.168.0.0/24 (which is on eth1 as I understand) and whose destination is 192.168.1.0/24 is dropped
I'm not 100% sure on this but once a packet is dropped no further rules are parsed ...
this seems exactly what you are complaining about.

Just as proof of concept :
if you flush your iptables do the 2 networks inter-operate but no internet ?

---

### Post by MrXpress on 2009-09-17
> **louigi600 said:**
> 
Just as proof of concept :
if you flush your iptables do the 2 networks inter-operate but no internet ?

Erm... wow. 

I flushed the tables, and... everything works! It wasn't what I envisioned the solution to be, but hey, I'm not complaining. Thanks a ton for your help.

---

