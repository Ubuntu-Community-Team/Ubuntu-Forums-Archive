---
title: "simplest way to set up local cname"
date: 2011-04-18
forum: Networking &amp; Wireless
---

### Post by peter360 on 2011-04-18
I wonder what would be the simplest way to set up a cname record on ubuntu?

I ran into a situation where I want to set up a cname alias hostA -> hostB on a ubuntu box.  I know I can set up local dns server(such as bind) or dns forwarder(such as dnsmasq) and point my /etc/resolve.conf to localhost.  

But I am wondering if there is even an easier way, as I really just need to make this one alias and it only needs to work on one box.  If hostB was a static ip address, I could have just put a line in my /etc/hosts, but afak /etc/hosts doesn't allow you to specify cname aliases.

---

