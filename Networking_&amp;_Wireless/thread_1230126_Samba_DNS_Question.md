---
title: "Samba DNS Question"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by Mr_Lazy on 2009-08-03
Hi,

I have been using Samba to connect to my works Windows network for about nine months and then it just stopped working. I was getting the "Could not open location" error after it has timed out.

The network admin guy asked me to check that I had the right DNS and gave me some IP addresses. Using the IP addresses I can connect using samba, but my question is, does Ubuntu cache the DNS settings and it is using old IP addresses? If so, how do I flush the old settings out?

Thanks in advance,

Mr L

---

### Post by dmizer on 2009-08-03
By default, Ubuntu uses the router as its DNS server. You can change the DNS servers via GUI, but to be honest, I'm not sure how. It's pretty easy to do via CLI though.

Just edit /etc/dhcp3/dhclient.conf like so:
```
gksudo gedit /etc/dhcp3/dhclient.conf
```
Look for the line that says "prepend domain-name-servers" and remove the # symbol. Add the DNS servers your network admin guy gave you so it looks something like this:
```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```
Replace 208.67.222.222 and 208.67.220.220 with the numbers he gave you (tip: make sure that there is no space before or after the comma separating the two DNS server addresses).

---

### Post by Mr_Lazy on 2009-08-03
dmizer,

Thanks, that worked a treat :)

OK, so a general question, will that router update itself? Or is this a specific question for my network guy?

Mr L.

---

### Post by dmizer on 2009-08-03
> **Mr_Lazy said:**
> dmizer,

Thanks, that worked a treat :)

OK, so a general question, will that router update itself? Or is this a specific question for my network guy?

Mr L.
No, actually the DNS servers that your network guy gave you are not the router. Those DNS servers will likely never change, so the above fix was a "do it and forget about it" fix.

What you did was override the Ubuntu default (which is to query the router for DNS resolution) and instead forced Ubuntu to query the DNS servers that your network guy gave you. The DNS servers that your network guy gave you are likely dedicated servers rather than routers.

---

