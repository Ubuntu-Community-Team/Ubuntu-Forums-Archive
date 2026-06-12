---
title: "primary &amp; secondary DNS server + dig"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by oliv66 on 2009-07-01
Hi all,

I have a modem/router/switch. My router is also my DHCP server even though I choosed a fixed IP address for one computer.

under /etc/resolv.conf I can see 192.68.1.1 which is the address of my gateway, not the address of my provider's DNS server

I would like to know the iP addresses of my DNS servers. I know how to find that information through my gear but not with dig or nslookup.

I tried dig @ns.myprovider.com  + a few more options with no success.

How could I get the real IP adresses of my provider's primary & secondary DNS servers ?

Thanks for your help,

Olivier

---

### Post by t0mppa on 2009-07-01
Well, I don't know about dig or nslookup and while learning the workings of new commands is always enlightening, just seems you're going at it the hard way. Why not simply check your routers configuration? The servers should be listed there. Or if you can't find them there, then just calling your ISP's tech support and asking them for the IP's?

---

### Post by MaindotC on 2009-07-01
The ISP's nameserver information should be in your access point (that's the proper name for this thing you call "modem/router/switch").  Just log into the access point and find the information it receives via DHCP.

---

### Post by oliv66 on 2009-07-02
Thanks for your reply.

Yes, I have my DNS servers through my Modem/router but I thought it was possible to collect with dig.

Olivier

---

### Post by puppywhacker on 2009-07-02
the resolver never knows the real DNS server from your provider, it uses the access points dns-proxy instead.

---

### Post by oliv66 on 2009-07-02
many thanks for this clarification.

---

