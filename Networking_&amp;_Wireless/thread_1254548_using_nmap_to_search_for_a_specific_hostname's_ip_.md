---
title: "using nmap to search for a specific hostname's ip address"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by pythonscript on 2009-08-31
I'm trying to set up ssh on my computer so I can ssh into it from any computer lab on campus, but my school's networks use dynamic ip allocation, so I thought I'd use nmap. How can I use nmap to search for a specific hostname on the LAN? I thought about just pinging everything on the network and maybe using a grep search? but would that register as a threat to the servers controlling the lan? Thanks!

---

### Post by pythonscript on 2009-09-06
Is nmap not the program to use for this?

---

### Post by falconindy on 2009-09-06
> **pythonscript said:**
> I'm trying to set up ssh on my computer so I can ssh into it from any computer lab on campus, but my school's networks use dynamic ip allocation, so I thought I'd use nmap. How can I use nmap to search for a specific hostname on the LAN? I thought about just pinging everything on the network and maybe using a grep search? but would that register as a threat to the servers controlling the lan? Thanks!
nmap isn't the tool you're looking for.

Your school's network may use DHCP, but they may not register hostnames with DNS. If this is the case, there's really not a whole lot you can do. What's wrong with using the dynamic DNS service I suggested?

---

### Post by pythonscript on 2009-09-06
> **falconindy said:**
> What's wrong with using the dynamic DNS service I suggested?

To use the top level domain name I already own, the services aren't free, and if possible, I'd like something that's self contained on my laptop and nowhere else. I still planning on looking into those. I guess it comes down to whatever I can get to work.

---

### Post by falconindy on 2009-09-06
I assure you, dyndns **does** offer a free dynamic redirect service. I personally use one to do exactly what you're trying to do here.

---

### Post by pythonscript on 2009-09-06
> **falconindy said:**
> I assure you, dyndns **does** offer a free dynamic redirect service. I personally use one to do exactly what you're trying to do here.

Do they offer a free service for a *top-level domain name*? I found on their website where they offer their free service for their subdomains (*mydomain*.dyndns.org, etc) but I was hoping to find something where I could use one of my spare level top level domain names.

---

### Post by falconindy on 2009-09-06
Hmm, just throwing it out there... do you have the ability via your nameserver host to redirect a CNAME to an ANAME? In other words, could you make an entry that would direct traffic to 'machine.myowndomain.com` to `somedyn.dnsdomain.com`?

You'd still have to use dyndns, but this is the only way I can think of to get a "free" redirect via your own TLD.

---

### Post by pythonscript on 2009-09-06
Yes, my nameserver does. It looks like I'll probably be working with the subdomain. It seems like it will save me trouble. I really appreciate the help, though. Thanks!

---

### Post by bear24rw on 2009-09-06
ping hostname

will resolve the ip..

---

### Post by falconindy on 2009-09-06
> **bear24rw said:**
> ping hostname

will resolve the ip..
Except that on a university domain, they may not track hostnames via their internal DNS. Most larger resnets won't. Hence his whole debacle...

---

