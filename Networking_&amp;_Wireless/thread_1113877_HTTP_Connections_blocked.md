---
title: "HTTP Connections blocked"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by meggark on 2009-04-02
Hi all.

Last night everything worked fine, and I didn't install or update any software at all. This morning I can no longer access the internet via my ubuntu (actually xubuntu) desktop. However I can ping successfully (hostnames and IPs so I'm guessing it's not a DNS issue). It just seems to be http that's the problem. If I try wget it just says "HTTP request sent, awaiting response..." and sits there indefinately, no timeout error, same with firefox and opera. I can't access anything, even the router control panel, via IP addresses either, only ping works. There were a couple of occasions where firefox got as far as loading the title of the pages and maybe 1 link at the very top of the page, but never further.

The machine is running Xubuntu 8.10 and is connected to the router (BTHomeHub - which is crap!) via a usb wireless dongle. It does not have a firewall installed, I've tried executing "iptables --flush" and all the usual rebooting of the machine and router to no avail. The hosts file is still in its default state also. There are no proxies involved either.

It work's fine from my dad's machine running windows connected via ethernet and my netbook running xubuntu via wireless.

Any ideas? I'm all out...Any replies appreciated as my final disseration for uni is due and I kinda need internet access before I can go much further.


Cheers

---

### Post by superprash2003 on 2009-04-02
post output of ifconfig from the terminal, it could be because you have a low MTU value. also htp://74.125.45.100 doesnt open completely right?

---

