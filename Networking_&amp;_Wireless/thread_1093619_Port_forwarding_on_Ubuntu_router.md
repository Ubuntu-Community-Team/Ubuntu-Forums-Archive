---
title: "Port forwarding on Ubuntu router"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by skidz on 2009-03-11
Hey all...

I have set up a router on an old machine running Ubuntu and everthing works great except, can't get port forwarding to work.

using this site: [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)
as a guide I did place this in my firewall script:
```

$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -p tcp --dport 80 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A PREROUTING -t nat -p tcp -d $EXTIP --dport 80 -m state --state NEW,ESTABLISHED,RELATED -j DNAT --to 192.168.1.107:80

```
With the goal of forwarding all incoming traffic on port 80 to 192.168.1.107.. where I host a couple websites.

I am new to this level of detail on networking, and find myself scratching my head as to reasons this might not work...

Maybe... the reason might be because I have installed bind, and I have to add a new zone for the domains I host behind the router? 

Please.. if someone just could point me in the right direction I really would appreciate it.

---

