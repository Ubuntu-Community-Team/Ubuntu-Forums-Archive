---
title: "Defaulting to web server when opening browser"
date: 2012-06-28
forum: Networking &amp; Wireless
---

### Post by M4DM4DZ on 2012-06-28
Hey guys,

How do i configure my local DHCP server/web-server so  users are brought to my homepage after obtaining an IP address and  opening their browser? 

eg, user plugs into switch, gets an IP,  opens web browser, instantly see's my webserver..... without typing in  any url into the address bar.

(This is a LAN only configuration)

Details:
Webserver 10.10.1.1 running on port 80 and 443
DHCP server running on same address, 10.10.1.1

---

### Post by asmoore82 on 2012-06-28
Easy - you can't.

If you're only talking about machines that you fully control, you could set some policies to enforce your homepage, but it's not something that would come from your DHCP server.

The only thing that would come close to doing this to any random machine would be to have your DHCP handing out itself as the DNS server; then your machine would have to be running a DNS server hacked up in such a way that every page resolves to your page. And even then it would only work for folks whose homepage is a plain old port 80 HTTP page , anyone who had set their homepage to an HTTPS site would likely see a "Connection Untrusted" message.

---

### Post by M4DM4DZ on 2012-06-29
Thanks man, I thought it would have somthing to do with DNS, I was wondering if it could be done with IPtables, but i'll sus it out....

Cheers

---

