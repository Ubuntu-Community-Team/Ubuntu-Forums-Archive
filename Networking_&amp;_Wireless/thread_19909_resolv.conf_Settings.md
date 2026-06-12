---
title: "resolv.conf Settings?"
date: 2005-03-14
forum: Networking &amp; Wireless
---

### Post by Uta on 2005-03-14
search
nameserver
nameserver

These are my options and not sure what I should enter. 

I am in a DHCP environment, my router address is 192.168.0.1, ISP is comcast.net

So should it be:
search comcast.net
nameserver 192.168.0.1

Thanks in advance!
 :?:

---

### Post by alastair on 2005-03-14
Yes - that's probably fine. But the proof is .. if it works. Assuming your router acts as a DNS cache (or forwards queries) this should be OK. Try pinging something you haven't visited e.g.

ping [www.cisco.com](www.cisco.com)

(or whatever).

---

### Post by Uta on 2005-03-14
That didn't work.

In a DHCP situation
to fill in this info for the resolv.conf

search
nameserver
nameserver

What should it be?
again my provider is comcast.net
and my local router is 192.168.0.1

Again, Thanks for your help!

---

### Post by haselden on 2005-03-16
I have comcast and my nameserver is:
search had1.or.comcast.net

I'm in oregon..guessing the .or. might be for oregon, though i wouldn't think it matters.

---

### Post by az on 2005-03-16
Isn't resolv.conf rerwritten by dhclient on connection anyway?

---

### Post by Uta on 2005-03-16
Yes, that was my understanding, but I have noticed my isn't?

First let me explain my somewhat odd situation... My Linux is running in a virtual environment on a Mac G4. The G4 is connect to the router via an ethernet cable. My consants are the router's address, 192.168.0.1 and that my provider is comcast.net.

I am getting an Internet connect, it just takes forever to do name resolves?
I thought perhaps there might be some way to speed up the name resolve situation?
Thank you again in advance for your help--

---

