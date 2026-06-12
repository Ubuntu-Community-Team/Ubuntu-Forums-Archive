---
title: "Bind DNS server IP range of clients to point to single IP on all DNS requests"
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by dainiookas on 2009-01-08
Hi,
There's a DHCP server in my network, which will give specific IP's to clients. The thing I want my BIND server to do is to decide next thing:
If my client has an IP adrress in a range, which is specified in BIND then BIND points him to single web page, no matter what request he makes.
If my client has a different IP (not in the specified range) then BIND works for him just as it should, providing IP's for all desired hostnames...

I have a situation like that and I'm very much interested on how can I make it. Maybe somebody can at least tell how can this options be called or smth, because currently I've only theoretical thoughts about my needs

Cheers!

---

### Post by kidders on 2009-01-09
Hi there,

> **dainiookas said:**
> If my client has an IP adrress in a range, which is specified in BIND then BIND points him to single web page, no matter what request he makes.

Afaik, you can't make a DNS server lie selectively, depending on where a request is coming from. The best you could do would be to configure Bind to *reject* requests from certain IPs (ie with an ACL). I doubt a server that can be made to distribute inconsistent or contradictory DNS information would ever be written ... that kind of thing can wreak havoc on a network!

In any case, the measure would be ineffective if, for some reason, a user outside the specified IP range didn't need to use your DNS server to visit a website (eg the relevant IP address was already in a local cache, in the user's head, or available from a different DNS server).

What you're trying to do sounds more like a job for a firewall than a DNS server. Iptables, for example, can be configured to forward all HTTP packets passing through it to a specific web server, regardless of where they're addressed. Something like this would do the trick ...```
iptables -t nat -I PREROUTING -s 192.168.100.0/24 -p tcp --dport 80 -j DNAT --to 12.34.56.78
```

I hope that helps. One other thing I should mention is that you'll really only be able to direct someone to a particular web *server* ... not a web page.

---

