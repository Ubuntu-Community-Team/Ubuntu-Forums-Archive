---
title: "(non-Ubuntu question).  VNC works with DynDNS, but firefox doesn't?"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2009-11-07
So I have a computer functioning as a server at home.  It listens for VNC, SSH and now HTTP requests as I recently installed Apache.  Now, I happen to be on the opposite side of the planet from where this computer is located.  I often VNC into my machine from here using the command line and have never had a problem connecting.  Testing the server over the VNC connection and watching from here showed that the Apache server is working.  I can even see the new HTTP site from a seperate computer, so my network port forwarding and all is fine.

Now, when I try to use Firefox on the computer I have here with me (on the other side of the planet), it never works.  UNLESS, I tell Firefox to use a SOCKS 5 proxy via an SSH tunnel to the server I use on rare occasion.

So basicly, I've encountered an oddity that I would suspect is related to the DNS server I use to access the Internet.  It resolves the DynDNS hostname to my home PC just fine when I use vncviewer in the terminal to access my home machine.  But it fails to resolve the hostname with the server's IP, unless I bypass it entirely and use my home ISP's DNS server.  The way I confirmed this was to use Firestarter on the server to block port 80, and then watch for an event to take place.  It blocked the local server as I expected, but never saw a single request arrive from me and my geographically distant location.  Why might it work for VNC and SSH connections but not for HTTP?

---

### Post by Dr. C on 2009-11-07
Does your ISP at home block ports? Many do and port 80 is a common one to block. I would try Firefox on a non standard port.

---

### Post by diablo75 on 2009-11-07
> **FineE said:**
> Does your ISP at home block ports? Many do and port 80 is a common one to block. I would try Firefox on a non standard port.

Yup that was it.  A buddy of mine just came online and he did the LAMP thing a few months ago, discovered the same problem.  I totally forgot the ISP blocked that port.  (Hangs head in shame)

---

