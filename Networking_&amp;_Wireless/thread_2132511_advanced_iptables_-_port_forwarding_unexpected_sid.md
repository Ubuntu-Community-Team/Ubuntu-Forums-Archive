---
title: "advanced iptables - port forwarding unexpected side-effect"
date: 2013-04-05
forum: Networking &amp; Wireless
---

### Post by stlu on 2013-04-05
I've intentionally made a busy home network so I'm forced to learn new things... only problem is now I gotta explain it to you clearly...


The network looks like this:

```

Internet Gateway - Wireless
192.168.2.1
    |
    | -----> 192.168.2.18 wlan0 [GATEWAY-PC(Iptables problems here)] 172.16.1.1 eth0 ---------------> 172.16.3.3 [SSHD-PC]
    |                                                              172.24.1.1 eth1 ---------------> 172.24.200.10 [TEST-PC]
    |
     \ ----->  192.168.2.22 wlan0 [LAPTOP]

```


I have here an iptables rule on a ubuntu server (GATEWAY-PC) that currently works for it's intended use.  No problems there.  Traffic coming in from the internet on port 22 is directed to a system running sshd (SSHD-PC).

```
stlu@gateway-pc$ iptables -A PREROUTING -t nat -i wlan0 -p tcp --dport 22 -j DNAT --to 172.16.3.3:22
stlu@gateway-pc$ iptables -A FORWARD -p tcp -d 172.16.3.3 --dport 22 -j ACCEPT

```


Tonight I tried to route traffic through this system from a client (LAPTOP) to another system (TEST-PC) such as:

```
stlu@laptop$ sudo route add -net 172.24.0.0/16 gw 192.168.2.18
```

I tried to ssh into TEST-PC, but instead, iptables rule took over and sent me to the SSHD-PC.  

I had hoped that the connection would be forwarded to the 172.24 network because that was the destination address.  However this iptables rule is applying itself to traffic that should be routed locally -- without DNAT.

The traffic that I want port-forwarded should be coming from my Internet Gateway into wlan0 with a destination address which will only ever be 192.168.2.18, while the traffic that I DON'T want port-forwarded will have other addresses (172.x) that can be routed locally through the ethernet interfaces, even traffic to other machines on port 22.

Thanks for any tips, this is a learning project and you're helping me learn!

tl;dr: 
Internet > GATEWAY-PC :22 > SSHD-PC  success.
Laptop > GATEWAY-PC > TEST-PC fail.

---

### Post by SeijiSensei on 2013-04-05
If you want to route traffic between the 172.x networks, use their respective gateways in the routing command, not the 192.168.2.18 address.  Presumably the gateway has a 172.16.3.x address assigned to eth0 and a similar address on eth1.  Machines on either of those subnets should use the address of the gateway they face. So if eth1 on the gateway is 172.24.200.1, the routing statement on TEST-PC would read:

```
sudo /sbin/ip route add 172.16.3.0/24 via 172.24.200.1
```

However it seems likely that 172.24.200.10 should already have 174.24.200.1 as its default gateway which makes the above rule redundant.  

You're not trying to use bridging across the interfaces by any chance?  Bridging and routing don't mix, and the first should be avoided except in rare circumstances.  IP routing is a much more reliable and logical method.

Make sure /etc/sysctl.conf has net.ipv4.ip_forward set to yes.  If you're still having problems, add some explicit FORWARD rules like

```
/sbin/iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT
/sbin/iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
```

---

### Post by stlu on 2013-05-04
SeijeiSensei, I have failed to be clear enough.

-First, there are NO problems on ANY of the networks.  Machines can ping each other with success.

-The only problem is that my Iptables rules on this Gateway-PC assume (wrongly) that everything coming in on the wireless side is originated from the internet, through the Internet gateway.  This is because I never had any other wireless device before now.

-Now I am trying to use a laptop to access the network by telling the laptop the route to 172.24.x. 

-When a ssh connection is attempted wirelessly from my laptop through the Gateway-pc, it mistakes it for internet traffic and applies the FORWARD rule for internet traffic on port 22, sending me to the wrong pc.

-I need to change the iptables rule so that all internet requests on port 22 are redirected, but anything from the 192.168.2.x network should be unchanged.

Here is a sketch of what I need my rules to do:
[U]
Needed Gateway-PC rules[/U]

1. any traffic inbound on wlan0 from addresses 192.168.2.x should be forwarded without any changes in the destination address or port.

2. any other traffic inbound on wlan0 should be subject to the IPTables rules that I have displayed in my earlier post.

---

### Post by stlu on 2013-05-04
Hurray, I found the answer:

> stlu@gateway-pc$ sudo iptables -t nat -I PREROUTING 1 **--source ! 192.168.2.0/24** -i wlan0 -p tcp --dport 22 -j DNAT --to 172.16.3.3:22



-"-I PREROUTING 1" inserts the rule first, so no other rules can mess with it.  Several on-line tutorials all use -A to add to bottom of list, but in my case I wanted it at the top to make sure no other rule was messing with it (I have quite a few rules and I don't fully understand how they may or may not conflict)

-"--source" followed by the exclamation mark, is a way of excluding a certain address or network.  I can't specify the source as "internet" just like that, but I can get the job done by applying the rule to all the many source addresses except for the 192.168.2.0 network.

-I had a thought that by using "--source 192.168.2.1" which is the address of the Internet Gateway, it would be a way to identify traffic coming from the internet... silly me, just because it comes through that device doesn't change the source address!

-I deleted the FORWARD rule, and all I seemed to need was this one line to make it work.  This is probably because I have customized /proc/sys/net/ipv4/ip_forward to be always set to 1, if it was at its default 0 then the FORWARD might be necessary.

-This also fixed another annoyance, that when I tried to ssh into gateway-pc directly on port 22, it also sent my request to the SSHD-PC.  I had fixed this by adding another port to sshd_config on gateway-pc, but yay now it just works!

-I realized that when I reboot my laptop, the routes will be lost.  Just a note in case it causes other people problems.

---

