---
title: "Jaunty, Network Manager, Wired, Wireless, Oh My..."
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by xefialtis on 2009-07-31
SO, I got this new T500 (Lenovo) and installed Jaunty on it, 2x now, just so I was sure I had a clean install because of some of the problems I have been having.

Network Manager shows several WIRED networks, and I cannot get rid of them.
ifupdown (eth0)
ifupdown (vpntun0)
ifupdown (test)

There is no way to delete these.

I have 2 wireless cards in this machine, 
AR5008
and a
Intel Pro 5100 AGN

They are both recognized, and both were "active" at one point.

I tried to create a New Wireless Connection for the AR5008 - we are using WPA2 Enterprise, but it wasn't one of the selections. 
I tried WPA2 Personal, and it couldn't connect due to the missing CERT, but kept asking me to validate some generic cert, and I clicked CANCEL, now I don't have any wireless...both Wireless Cards say "wireless is disabled"...

So, as you can see, I want to fix this, I want to get into whatever file, conf, xml, list, or whatever, and REMOVE the unwanted WIRED connections and set up the WIRELESS connections so they work.

Any ideas on where to start?

---

