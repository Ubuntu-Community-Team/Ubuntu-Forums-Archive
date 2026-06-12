---
title: "Xbox, iptables, port forwarding"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by ~Niebr~ on 2009-10-07
Alright, so I got connected with xbox live through a series of iptables commands, but heres the problem that it seems like all ubuntu users have, NAT! 

So I dove deeper and tried to fix it myself using the Terminal, which went good for all of about 5 mins, The first line of code i put in was this 

```
$ iptables -t nat -A PREROUTING -i $WAN_IF -p tcp --dport 3074 -jDNAT --to-destination 192.168.2.2
```and got this

```
Bad argument `tcp'
Try `iptables -h' or 'iptables --help' for more information.
```Heres the whole thing, if someone can tell me what i am doing wrong, that would be a great help, thanks!

Heres the whole thing:
```
 $IPTABLES -t nat -A PREROUTING -i $WAN_IF -p tcp --dport 3074 -j DNAT --to-destination $XBOX_IP
   $IPTABLES -t nat -A PREROUTING -i $WAN_IF -p udp -m multiport --dports 88,3074 -j DNAT --to-destination $XBOX_IP
   $IPTABLES -A FORWARD -i $WAN_IF -d $XBOX_IP -p tcp --dport 3074 -j ACCEPT
   $IPTABLES -A FORWARD -i $WAN_IF -d $XBOX_IP -p udp -m multiport --dports 88,3074 -j ACCEPT
```

---

