---
title: "DNS Resolution in Terminal"
date: 2012-06-25
forum: Networking &amp; Wireless
---

### Post by josehp603 on 2012-06-25
I am working for a company and I am behind a proxy, I have my global proxy settings configured in my computer and my internet browsers and applications are able to connect to the internet and resolve dns queries. My http_proxy variable has the correct proxy settings.

My problem is that when I do something like:

>>> import socket
>>>socket.gethostbyname('www.ubuntuforums.org')

it gives me the error No address associated with hostname because my socket can't connect through the proxy to access external webpages. I can only resolve our local websites.

I have the same problem if I use dns.resolver

>>>import dns.resolver
>>>answers = dns.resolver.query('www.internalwebsite.com',
dns.rdatatype.A)
>>>

That works, but if I try to resolve a website like ubuntuforums it gives me dns.resolver.NXDOMAIN error.

Does anyone have a clue on how to solve this, how to make my dns queries go through the proxy server, thus obtaining the IP address. I really need to solve my dns inquiries using the
dns.resolver.query , it is part of a company project to do some testing we need to do, I also tried using dnsmasq with no luck.

Thanks all in advance

---

### Post by rukiaEnix on 2012-06-25
Do you have the right DNS settings at /etc/resolv.conf?

Also add this google DNS and check if you can resolve external sites:

```

nameserver 8.8.8.8
nameserver 8.8.4.4

```

---

### Post by josehp603 on 2012-06-26
No it does not work, the problem is not my DNS server, the problem is that my terminal, the problem is that when I try to use commands as dns.resolver.query... or socket.gethostbyname(...) they can't connect through my company's proxy server to resolve the hostnames into their corresponding IP's. I tried using a local dns server (dnsmasq) and it didn't work either.

---

### Post by rukiaEnix on 2012-06-26
Why don't you try with the command nslookup or dig?

---

### Post by asmoore82 on 2012-06-26
A little off but a useful tidbit of info...

You can force `dig` to use any DNS on the fly with the at symbol "@".
And dig with no parameters looks up the root dns servers. In this way you can walk the DNS path back to the authoritative answer.

```
**$ dig**
;; ADDITIONAL SECTION:
f.root-servers.net.	75761	IN	A	192.5.5.241
f.root-servers.net.	75761	IN	AAAA	2001:500:2f::f
h.root-servers.net.	75761	IN	A	128.63.2.53
h.root-servers.net.	38763	IN	AAAA	2001:500:1::803f:235
**$ dig www.google.com @192.5.5.241**
;; ADDITIONAL SECTION:
a.gtld-servers.net.	172800	IN	A	192.5.6.30
b.gtld-servers.net.	172800	IN	A	192.33.14.30
**$ dig www.google.com @192.5.6.30**
;; ADDITIONAL SECTION:
ns2.google.com.		172800	IN	A	216.239.34.10
ns1.google.com.		172800	IN	A	216.239.32.10
**$ dig www.google.com @216.239.32.10**
;; ANSWER SECTION:
www.google.com.		604800	IN	CNAME	www.l.google.com.
www.l.google.com.	300	IN	A	74.125.137.105
```

Presumably the forced proxy is for security; but if these `dig`s work it's just an inconvenience.

---

### Post by josehp603 on 2012-06-26
Thanks for the info, nslookup or dig neither work,they give me the same NXDOMAIN error for external websites I can't seem to figure out what is that I don't have configured correctly

---

### Post by rukiaEnix on 2012-06-26
Excuse me for insisting but why don't you try using other DNS in your resolv.conf configuration just to see if it really is the terminal as you say.

---

### Post by josehp603 on 2012-06-26
I have tried other DNS services, and all my apps (firefox, chrome, etc) work with the current setup, it's just the terminal that does not go through the proxy or maybe the dig, nslookup, dns.resolve command are not compatible at all with http proxy

---

### Post by rukiaEnix on 2012-06-26
OK, the problem is that you Internet traffic at your work is blocked.
You just have LAN connection.

With browsers you have Internet traffic because of the proxy, so you will never resolve outside your network without going through a proxy.

To verify this ping to the IP address of an external site like ubuntuforums

And if the things I said before are correct, we have to find a way of making DNS Resolution applying your correct proxy settings.

---

### Post by josehp603 on 2012-06-26
Yes, here is my terminal output when I ping an internat site:

PING [www.XXXX.com](www.XXXX.com) (10.4.1.14) 56(84) bytes of data.
64 bytes from 10.4.1.14: icmp_req=1 ttl=122 time=1.77 ms
64 bytes from 10.4.1.14: icmp_req=2 ttl=122 time=6.19 ms
64 bytes from 10.4.1.14: icmp_req=3 ttl=122 time=1.78 ms
64 bytes from 10.4.1.14: icmp_req=4 ttl=122 time=1.73 ms

And here is when I try to ping ubuntuforums

ping: unknown host [www.ubuntuforums.org](www.ubuntuforums.org)



> **rukiaEnix said:**
> OK, the problem is that you Internet traffic at your work is blocked.
You just have LAN connection.

With browsers you have Internet traffic because of the proxy, so you will never resolve outside your network without going through a proxy.

To verify this ping to the IP address of an external site like ubuntuforums

And if the things I said before are correct, we have to find a way of making DNS Resolution applying your correct proxy settings.

---

### Post by rukiaEnix on 2012-06-26
Please ping the ubuntu forums IP:

```

ping 91.189.94.12

```

---

### Post by josehp603 on 2012-06-27
I get the request timed out error

> **rukiaEnix said:**
> Please ping the ubuntu forums IP:

```

ping 91.189.94.12

```

---

### Post by rukiaEnix on 2012-06-27
Then you don't have direct Internet connection, as I told you it is blocked, allowing only traffic that comes from the proxy.

So the thing we have to look then is, if there is a way of resolving passing the proxy address as a parameter

---

### Post by josehp603 on 2012-06-27
That is what I've been trying to do but apparently dig, nslookup, dns.resolver use ICMP which is a protocol not compatible with HTTP Proxy, so probably I won't be able to find a "work around" for this.

> **rukiaEnix said:**
> Then you don't have direct Internet connection, as I told you it is blocked, allowing only traffic that comes from the proxy.

So the thing we have to look then is, if there is a way of resolving passing the proxy address as a parameter

---

### Post by rukiaEnix on 2012-06-27
Sorry for this question but, why do you want to resolve from your terminal? I mean obviously we always want things to work right but, do you have a particular purpose?

---

### Post by asmoore82 on 2012-06-27
Obviously I've heard of proxies before, and I've heard of transparent server side DNS proxies; but I've never heard of forced client DNS proxies before.

Some quick googling seems to indicate that only SOCKS proxies support proxying of DNS queries.

If that sounds familiar to you, you could try this:
```
$ export all_proxy=socks://<*your_proxy_info*>/
$ dig www.google.com
```

---

### Post by josehp603 on 2012-06-28
The reason is that I am trying to do some simulations and tests using an open source project called web-page-replay, and it needs to do DNS resolution to work. I gave up working on this I'll see if IT gives me a non-proxy connection. Thanks all for your help

> **rukiaEnix said:**
> Sorry for this question but, why do you want to resolve from your terminal? I mean obviously we always want things to work right but, do you have a particular purpose?

---

