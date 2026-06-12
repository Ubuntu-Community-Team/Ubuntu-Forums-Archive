---
title: "Simple NAT issues"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by grimstoner on 2010-06-07
Hi

I want to do something that should be simple... NAT a certain port to an IP on my network. *rant about how much I've tried, googled and failed*

Our building has assigned us an IP Range (say, 10.0.0.x). They've also provided me with 1 public IP, which they NAT to an IP in that range of my choice (say, 10.0.0.50). I want to NAT port 6500 on that IP, to a different IP's port 80 (10.0.0.51:80) (i.e. come in on 10.0.0.50:6500, forward all the packets to 10.0.0.51:80).

I've reset my firewall in Webmin, so it looks like this :

**Packet filtering : Input (Default Drop)**
```
Accept	If input interface is not eth1		
Accept	If protocol is TCP and TCP flags ACK (of ACK) are set		
Accept	If state of connection is ESTABLISHED		
Accept	If state of connection is RELATED		
Accept	If protocol is UDP and destination port is 1024:65535 and source port is 53		
Accept	If protocol is ICMP and ICMP type is 0		
Accept	If protocol is ICMP and ICMP type is 3		
Accept	If protocol is ICMP and ICMP type is 4		
Accept	If protocol is ICMP and ICMP type is 11		
Accept	If protocol is ICMP and ICMP type is 12		
Accept	If protocol is TCP and destination port is 22		
Accept	If protocol is TCP and destination port is 113		
Accept	If protocol is ICMP and ICMP type is 8	
Drop	If protocol is TCP and destination port is 2049:2050		
Drop	If protocol is TCP and destination port is 6000:6063		
Drop	If protocol is TCP and destination port is 7000:7010		
Accept	If protocol is TCP and destination port is 1024:65535
```

**NAT Prerouting (Default Accept)**
```
Empty
```

I run these two commands :

```
iptables -A PREROUTING -t nat -i eth1 -p tcp --dport 6500 -j DNAT --to 10.0.0.51:80
iptables -A INPUT -p tcp -m state --state NEW --dport 6500 -i eth1 -j ACCEPT
```

Then, this is added to the Packet Filtering : Input chain :

```
Accept	If protocol is TCP and input interface is eth1 and destination port is 6500 and state of connection is NEW
```

and this to NAT : Prerouting :

```
Destination NAT	If protocol is TCP and input interface is eth1 and destination port is 6500
```

But still no luck... port still isn't forwarded, not on the local network, or from outside. I can still ssh, ping and access Webmin, so the firewall isn't blocking ALL requests. 

Can anyone please help me.

Btw... running Lucid.

---

### Post by grimstoner on 2010-06-07
Also, Forward and Output chains are empty, default policy ACCEPT.

---

