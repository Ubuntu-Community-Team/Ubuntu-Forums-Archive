---
title: "HTTP Error 400 &amp; Routing"
date: 2012-08-01
forum: Networking &amp; Wireless
---

### Post by CrimsonRider on 2012-08-01
I've got a really weird thing going on.

I have an Ubuntu proxy server in my home network. That runs an simple IPtables set to allow LAN Windows computers to get on the internet.

But, there are sites that simply don't cooperate with that. Here is my setup;

```
/sbin/iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
/sbin/iptables -A FORWARD -i eth1 -o eth0 -m state  --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT
```

Or like this;
```
iptables -L -v
Chain INPUT (policy ACCEPT 243K packets, 28M bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
29662   51M ACCEPT     all  --  eth1   eth0    anywhere             anywhere             state RELATED,ESTABLISHED
20914 2525K ACCEPT     all  --  eth0   eth1    anywhere             anywhere

Chain OUTPUT (policy ACCEPT 217K packets, 72M bytes)
 pkts bytes target     prot opt in     out     source               destination
```

Now i try to reach a site via one of the LAN computers, and it keeps refusing to load giving;

```
HTTP Error 400. The request is badly formed.
```

However if I load the site on the server itself, it's fine.
Also, when I use a squid proxy to load the site, it's fine.

What is going on here? Why is routing resulting in 400 errors?

---

### Post by Doug S on 2012-08-02
What you have looks O.K. to me. In terms of trying to help, I can only suggest what I would do next. First, and without a good reason why, I would try to change this line:```
/sbin/iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
```To this:```
/sbin/iptables -t nat -A POSTROUTING -o eth1 -j SNAT --to $EXTIP
```where $EXTIP is your external IP address (which even if it is dynamic, you should know for a test).
Next, I would make two tcpdump or wireshark sessions, one lookikng at internal packets and one looking at external packets. This would be to examine things at the packet level to try to determine what is going wrong.

---

### Post by CrimsonRider on 2012-08-19
Okay, still having this problem.

Nothing I tried so far has worked, and I am not quite sure how to capture one specific IP packet going to one specific site (politicalmachine.com) and have frankly NO idea whatsoever what the heck is going on here.

As far as I understand, the routing shouldnt change anything. But it does, any help from anyone?

---

### Post by Doug S on 2012-08-19
Try capturing packets on both interfaces and comparing, there should only be address translation differences. Example:```
doug@doug-64:~/temp1$ sudo tcpdump -n -nn -tttt -A -i eth1 host 74.204.71.223 >eth1
```and```
doug@doug-64:~/temp1$ sudo tcpdump -n -nn -tttt -A -i eth0 host 74.204.71.223 >eth0
```where 74.204.71.223 = politicalmachine.com

---

