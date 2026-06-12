---
title: "http over browser works but ssh/nslookup/ping do not work"
date: 2011-03-17
forum: Networking &amp; Wireless
---

### Post by arvinds on 2011-03-17
I am mostly new to ubuntu and networking.

I am able to browse the internet using my browser but anything else like trying to ssh/ping/nslookup does not work.

I believe it is a configuration issue where my network configuration and in particular my nameserver is not correctly specified but I don't know how to fix 
it.

Ping not working:
> 
$ ping [http://www.cnn.com](http://www.cnn.com)
ping: unknown host [http://www.cnn.com](http://www.cnn.com)


This ssh server was up when I tried this:
> 
ssh unix.andrew.cmu.edu
ssh: connect to host unix.andrew.cmu.edu port 22: Connection refused


Nslookup not working:
> 
$ nslookup [http://www.cnn.com](http://www.cnn.com)
Server:		128.2.1.11
Address:	128.2.1.11#53

** server can't find [http://www.cnn.com:](http://www.cnn.com:) NXDOMAIN


And finally, my /etc/network/interfaces file:
> 
auto lo
iface lo inet loopback


How come by browser can find [http://www.cnn.com](http://www.cnn.com) but ping can't?

---

### Post by varunendra on 2011-03-19
Everything is okay, just don't use "http://" in those commands. It only specifies the protocol to be used, not a part of domain hierarchy.

As for ssh command, I'm not yet familiar with it to be honest. Maybe google or "man ssh" command could help you.

---

