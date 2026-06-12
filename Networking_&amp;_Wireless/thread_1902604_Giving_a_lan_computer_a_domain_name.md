---
title: "Giving a lan computer a domain name?"
date: 2011-12-31
forum: Networking &amp; Wireless
---

### Post by simpsda on 2011-12-31
Hello all, I have been trying to give my Ubuntu 11.10 server a domain name. Preferably a sub domain, either or.

The reason I need to do this is because I have many applications (apache, ect) using the same port. I already have a domain pointing to my WAN address, where my main server is. Is this where a domain name server comes in? I do have dd-wrt firmware on my router, if that can do anything for me.

Sorry if I sound like a newbie :p

If anyone can help me thank you soooo much!

---

### Post by jamespetts on 2011-12-31
Some routers will let you assign domain names to local IP addresses - check your router's manual.

---

### Post by simpsda on 2011-12-31
Hmm thanks! I have checked out some documentation on a feature in dd-wrt called "DNSMASQ" but it is quite confusing. Is there any routers you recommend? :)

---

### Post by syerges on 2011-12-31
DNSMASQ is worth understanding if you are giving your pc's their own IP's... I suggest using it if it is compatible with Ubuntu.
> **simpsda said:**
> Hmm thanks! I have checked out some documentation on a feature in dd-wrt called "DNSMASQ" but it is quite confusing. Is there any routers you recommend? :)

---

### Post by fdrake on 2012-01-01
you want other computers on your LAN to access your pc server with a domain server instead of an ip-address? then:

- you will need to setup a local DNS server : search online it's a pretty rich subject amd you will need to take your time with it otherwise you will mess-up your LAN! :[http://www.aboutdebian.com/dns.htm](http://www.aboutdebian.com/dns.htm)

-or if your router has the option to act as a dns good then, problem solved..

- if you have only 2/3 pc in your lan (using linux) then efit the file /etc/hosts and add an entry with the ip-address of the server with the desired domain-name. You have to repeat this task for each pc!

---

### Post by simpsda on 2012-01-01
@fdrake I want to access a local computer with a domain from WAN and LAN :p
So that mydomain.com points to 192.168.1.*

What I am coming to realization is that I need to have
mydomain.com --> My WAN IP --> Handled by a DNS server --> To a server on my LAN
All of this ^^ Without port forwarding because of the applications I use have the same ports. (port 80, ect)

Is this possible?

I really appreciate this help btw.

---

### Post by Lars Noodén on 2012-01-01
> **simpsda said:**
> Hmm thanks! I have checked out some documentation on a feature in dd-wrt called "DNSMASQ" but it is quite confusing. Is there any routers you recommend? :)

[dnsmasq](http://thekelleys.org.uk) is a DHCP server and DNS forwarder.  Try looking at the documentation, it is very simple to configure.  I have used it a lot and find it quite useful.

It can be used to assign names to IP numbers used on your LAN.

---

