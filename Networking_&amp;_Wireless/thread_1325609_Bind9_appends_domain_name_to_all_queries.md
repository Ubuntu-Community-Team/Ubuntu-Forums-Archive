---
title: "Bind9 appends domain name to all queries"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by questioningquestioner on 2009-11-13
I have the following situation i was hoping someone could help me with.

When i do an NSLOOKUP in windows XP against my ubuntu BIND9 server, what is returned looks like this:

```

nslookup google.com


Server: Unknown
Address: 192.168.x.x

Name: DOMAIN.COM
ADDRESS: WAN address 24.x.x.x
**Aliases: google.com.domain.com**

```

As you can see, bind has appended domain.com to the query. The address returns as my internet gateway address and not the address of google, as I have a wildcard *.DOMAIN.COM in the zonefile for domain.com

Now I know why this is happening. I have a router/DHCP server which gives me a "connection specific DNS suffic" of domain.com 

If i set the same address manually on XP, this does not happen, as it does not have the suffix.

My unbuntu DNS bind server is athoritative for DOMAIN.COM.

Can someone please tell me what I am doing wrong on my name server to make in append the domain to the query?

Locally on the bind server, it does NOT do this, but that server is not on DHCP either so... 

Also if i nslookup google.com**.**  (note the extra **.** at the end) then it resolves correctly. I am sure that it is some kind of misconfiguration on my bind9 server. Anyone have any ideas?

---

