---
title: "what is crashing my router?"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by evgen88 on 2009-10-29
Ever since I brought an Ubuntu machine on my wired network my broadband router crashes at least once ever 2 hours. It is not pingable in this state, and has to be hard reset.

I thought ktorrent may be over loading it, but shutting that down didn't help.
It has actually been 2 different machines, a temporary laptop, and a homemade desktop.

Can anyone think of a process that might be sending unusual signals through the router?

The both machines also used the router for DHCP 

I can try fiddling around with manual IP config, and shutting down services, but as it can take up to 2 hours between freezes it's a slow process. 

I'm hoping for some possible sources to narrow it down.

The broadband router is a Buffalo Broadstation BBR-4MG is anyone is wondering.

The router has worked before introducing the machines to the network for months, and for days since removing them with no crashes.

---

### Post by evgen88 on 2009-11-01
wow, no one even has a guess?

Don't get me wrong, I know it is the cheap router's fault, but that was supplied by my internet provider, so I don't think I can replace it, and I don't really want to put out the money either.

---

### Post by coffeeaddict22 on 2009-11-02
Hi,
No idea.  Have you looked in the dmesg log just after a crash?  What kind of setup- wired or wireless?  Can you run the same machines in a different OS without trouble?  
There's a page [here]("http://www.linuxjournal.com/content/troubleshooting-network-problems") with some ideas on where to start troubleshooting, although from what you're saying it sounds like the problem may be a hardware setting.  What driver are you using, and what hardware is the PC running?

---

