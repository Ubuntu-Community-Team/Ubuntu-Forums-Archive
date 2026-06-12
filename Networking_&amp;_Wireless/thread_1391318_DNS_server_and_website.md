---
title: "DNS server and website"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by Rich78 on 2010-01-26
I'm looking to host some websites on a Xen VPS setup I've signed up to.  I've got 5 ip addresses to play with on the one server.

Should I consider transferring the DNS records to this machine or leave them with the provider I purchased the domain name from?  I have the facility to modify the DNS records with that provider so could point the domain to the above VPS.

However I could setup Bind9 on the VPS and have total control, but looking into it suggests I could loose two ips for the master and slave.  Although they would effectively be on the same box so be a little pointless as a redundancy.

Which brings me to the question of whether firstly having a DNS server and web server on the same box is a good idea?  I'm thinking no?

Secondly is hosting DNS records on a VPS a good idea?  again I'm thinking no?

---

### Post by gombadi on 2010-01-26
Short answer - leave the dns where it is

Longer answer -

> 
However I could setup Bind9 on the VPS and have total control, but looking into it suggests I could loose two ips for the master and slave. Although they would effectively be on the same box so be a little pointless as a redundancy.


Really bad idea to direct both nameservers to the same physical machine. Keep them as separate as possible.

> 
Which brings me to the question of whether firstly having a DNS server and web server on the same box is a good idea? I'm thinking no?


It will work fine from a Linux point of view. They are different processes doing different things. and of course you will have one of the dns servers on a remote machine won't you (see previous answer)

> 
Secondly is hosting DNS records on a VPS a good idea? again I'm thinking no? 


A VPS is fine for hosting ONE of the dns servers as long as you use some other machine for the second dns server - see previous two answers :-)

---

### Post by Rich78 on 2010-01-27
Thanks :D

---

