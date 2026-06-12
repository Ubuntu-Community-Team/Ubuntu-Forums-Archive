---
title: "DNS simpler than BIND"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by snorkytheweasel on 2009-03-30
Is there a simple DNS? BIND is very complicated and way over-powered for my simple networks. I'm using HOSTS, but every time I add a machine, I have to update the HOSTS file on each computer.

I don't need multiple zones and Start of Authority, etc. I just need DNS that keeps track of IPs and host names in one subnet, whether static or DHCP.

FWIW 
1) I use BIND on a complex network with several virtual hosts, and multiple physical servers but even with a GUI (in CentOS) it's a lot of work to set up. 

2) even using webmin it's more trouble than frequently updating HOSTS files.

---

### Post by capscrew on 2009-03-30
[**DNSmasq**]("http://thekelleys.org.uk/dnsmasq/doc.html")

---

### Post by snorkytheweasel on 2009-03-30
> **capscrew said:**
> [**DNSmasq**]("http://thekelleys.org.uk/dnsmasq/doc.html")

That sounds exactly like what I need. I'll try it & get back to you. 

"Seek and ye shall find."
-- JC (Matt 7-7)
-- Ella Fitzgerald (Someone To Watch Over Me)
 
"The search will bring the reward."
-- Frank Crippen [http://www.nxnwsurf.com/](http://www.nxnwsurf.com/)

"Google it yourself."
-- me

---

