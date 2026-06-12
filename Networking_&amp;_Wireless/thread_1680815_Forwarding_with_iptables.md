---
title: "Forwarding with iptables?"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by Nessaja on 2011-02-03
Hi.

I've got a problem that I just can't seem to get around of, and I'm sure it's simple.

So here's the problem, I want to forward all http traffic comming in from external ip 196.21.22.23 eth0 to an internal IP connected to eth1 eg. 10.0.0.5 port 3100, and when it goes back out it should be port 80 again on the external IP.

I know it's simple, Ive done it in the past, but for some reason it's not working at all...

I'm using iptables to do this.

```

iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -p 80 -j ACCEPT

iptables -A FORWARD -i eth0 -p 80 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to 10.0.0.5:3100



```

I did something wrong, but requests to the external IP's port 80 is not being routed to 10.0.0.5:3100

---

### Post by Nessaja on 2011-02-07
My Mistake,
The iptables rules were correct, however the ISP didn't enable the external IP yet, that's why it didn't work

---

