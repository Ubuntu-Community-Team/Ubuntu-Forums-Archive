---
title: "Outgoing redirection with iptables - TCP skips nat?"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by kristrev on 2009-03-19
Hello,

I am working on configuring a multihomed machine, and one of my goals is to redirect some outgoing TCP-traffic originating from this machine using iptables. Currently, I have got it working with UDP and if I add the rule to the output-chain of the NAT-table before I start the connection, it works.

However, sometimes I want to start doing redirection in the middle of a TCP connection and this does not seem to work. I do not get any matches to my LOG-target and the packets still go through the old interface. In other words, it somehow seems like TCP is skipping the NAT's output-chain. Does anyone have any ideas how to solve this?

The iptables rule I use is:
sudo iptables -A OUTPUT -t nat -p tcp -d 192.168.101.14 --dport 9999 -j DNAT --to 192.168.100.250:9999

Edited: Forgot to add, with my LOG-rule I only see the SYN-packets. To catch as much as possible I have made it very general:
sudo iptables -A OUTPUT -t nat -p tcp -d 192.168.101.14 --dport 9999 -m state --state NEW,ESTABLISHED,RELATED --sport 1024:65535 -j LOG --log-prefix "INFO,OUTPUT,NAT(tcp): " --log-level debug

Thanks in advance,
Kristian

---

### Post by mbfrog on 2009-03-19
kristrev,

At first sight, it could be related to conntrack, where packets for existing connectsions would match a previous rule and skip your DNAT rule.  Hard to say for sure without seing your whole iptables setup though.

---

### Post by regala on 2009-03-19
> **kristrev said:**
> Hello,

However, sometimes I want to start doing redirection in the middle of a TCP connection and this does not seem to work. I do not get any matches to my LOG-target and the packets still go through the old interface. In other words, it somehow seems like TCP is skipping the NAT's output-chain. Does anyone have any ideas how to solve this?



sorry, but this is not really solvable: it is a feature not a bug.
starting to redirect a TCP connection goes against the principle of NAT.
When the first packet of a connection is passed to the Netfilter stack, it is handled by the Nat/Conntrack code, which creates a connection handle for the whole connection. Redirection is applied and the "operation" is stored to be unapplied in the reverse way and applied in the right way.
then subsequent packets are "ignored" the Nat/Conntrack code which applies to them the Translation rules associated with the connection and then, they are passed directly to Filtering (the filter table).

What you ask is not handled by Nat which by definition tries to handle and preserve TCP connections, yet what you want is to initiate another TCP connection with another host. :)

I hope my explanation is understandable. Redirecting a TCP connection means reestablishing another connection, and so it means that it has to be done in userspace by your application, not by any network stack.

The best way to do it, is using the QUEUE target in the filter table

```

iptables --table filter (...) -j QUEUE

```

and have your application polling for this QUEUE and reestablish a new connection when the filter matches (I will look into it, as I have done such a thing just once and a quite long time ago)

---

### Post by regala on 2009-03-20
> **regala said:**
> 
```

iptables --table filter (...) -j QUEUE

```

and have your application polling for this QUEUE and reestablish a new connection when the filter matches (I will look into it, as I have done such a thing just once and a quite long time ago)

More on that: packets that are put into the QUEUE target by an iptables rule are passed to userspace, and can be used and manipulated, responded with any IPTables related answer (like NF_ACCEPT) and then can trigger any C action you need. You can then trigger a new ```
connect()
``` or create a new socket to establish a new connection. You have to use libipq from iptables. For more information, ```
man libipq
``` should give you all info you need.
But whatever you do, you cannot change the endpoints of a TCP conn, which would mean it is _another_ TCP connection.

br

---

