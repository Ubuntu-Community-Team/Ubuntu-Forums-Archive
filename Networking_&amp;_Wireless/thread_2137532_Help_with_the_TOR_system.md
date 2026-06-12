---
title: "Help with the TOR system"
date: 2013-04-21
forum: Networking &amp; Wireless
---

### Post by Cancellator on 2013-04-21
Hi, i'm interested in using the TOR network on Ubuntu. What I would like is:

Use TOR to encrypt ALL traffic, not just browsing.
AND have an easy way to switch it on/off.

How I would like it to work is "run magic command -> all my traffic goes through TOR -> run magic command -> TOR deactivated".

Is this even possible or am I asking too much? 
Thanks for your help!

---

### Post by Lars Noodén on 2013-04-21
There's a lot of traffic that should not be run through Tor.  Torrents are just one example.  

That said, Tor is just a SOCKS proxy so anything you can configure to run through SOCKS can be run through Tor.  If you want to be sure you're running through Tor, use IPtables or UFW to block any outgoing or incoming traffic except that on Tor's port.

About easy on/off, have you looked at Vidalia?

---

