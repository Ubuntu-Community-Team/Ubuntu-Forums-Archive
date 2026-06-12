---
title: "Forwarding ports to other, internal hosts"
date: 2012-10-05
forum: Networking &amp; Wireless
---

### Post by deadtom on 2012-10-05
Here is the setup. I have a kubuntu box, running iptables, acting a router/firewall.
Internal=eth0 192.168.1.1
External=eth1 DHCP
I am able to redirect ports for the server itself just fine, using this line in iptables.rules:
```
-A PREROUTING -p tcp -m tcp -i eth1 --dport 10008 -j DNAT --to-destination 192.168.1.1:80
```
This redirects traffic over port 10008 to port 80 just as it should. It also works for a variety of other ports with no problem, but only on the server itself.

What I want to do, is forward/redirect certain ports to ports on other, internal hosts. For example, I'd like 10009 to go to port 80 on one PC. I'd also like 10010 to go to 22 on another, and so on and so forth.

Here is the line I'm trying to use for that:
```
-A PREROUTING -p tcp -m tcp -i eth1 --dport 10009 -j DNAT --to-destination 192.168.1.26:80
-A PREROUTING -p tcp -m tcp -i eth1 --dport 10010 -j DNAT --to-destination 192.168.1.17:22

```
This portion doesn't work, for any port to any host on my network.

Here is the output of #iptables -t nat -L -n -v:
```
Chain PREROUTING (policy ACCEPT 1 packets, 313 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:10008 to:192.168.1.1:80
    0     0 DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:10009 to:192.168.1.26:80
    0     0 DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:10010 to:192.168.1.17:22
```

and #cat /proc/sys/net/ipv4/ip_forward:
```
1
```

I've tried it with and without explicitly allowing traffic in through those ports, using the code below, but it makes no difference.
```

-A tcp_inbound -p tcp -m tcp --dport 10009 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 10010 -j ACCEPT

```

Finally, here are the entries in my logs, showing what's happening to those packets when they come in:
```
Oct  5 10:14:45 server kernel: [940967.347905] FORWARD packet died: IN=eth1 OUT=eth0 SRC=x.x.x.x DST=192.168.1.17 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=17019 DF PROTO=TCP SPT=56730 DPT=5900 WINDOW=8192 RES=0x00 SYN URGP=0 

Oct  5 11:24:50 server kernel: [945172.710259] FORWARD packet died: IN=eth1 OUT=eth0 SRC=x.x.x.x DST=192.168.1.26 LEN=52 TOS=0x00 PREC=0x00 TTL=115 ID=6930 DF PROTO=TCP SPT=60250 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
```

I've made sure that there are no conflicting rules below these entries in my iptables.rules.

Can anyone see what I'm doing wrong?

---

### Post by Doug S on 2012-10-05
I think you are not providing a path for the forwarded packet through the FORWARD chain. There was a [similar thread ]("http://ubuntuforums.org/showthread.php?t=2065712")just the other day.

---

### Post by deadtom on 2012-10-05
> **Doug S said:**
> I think you are not providing a path for the forwarded packet through the FORWARD chain. There was a [similar thread ]("http://ubuntuforums.org/showthread.php?t=2065712")just the other day.

Yup! That did it. I had to add this line to my iptables.rules:

```
-A FORWARD -i eth1 -o eth0 -j ACCEPT
```Thank you!

---

