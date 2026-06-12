---
title: "ndiswrapper errors"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by avlinux on 2009-11-01
I used ndiswrapper to install the windows .inf driver to Ubuntu and I get an error saying that Ubuntu could not install the driver, immediately after this, it shows in the list that the hardware is present.  I've been trying to narrow down what exactly is causing these contradicting statements.  I found a post on a different forum showing me how to install this exact driver on 9.10 through commands rather than the application itself.  It starts by saying to install the driver via command, ndiswrapper -i /usr/joe/Desktop/drivers/net8190p.inf, after this command I get this:

couldn't create /etc/ndiswrapper/net8190p: Permission denied at /usr/sbin/ndiswrapper-1.9 line 194.

I was wondering if anyone can help me out with this.  I have an Encore Electronics ENLWI-NX2 pci card, the model / device id is, MCP77  10DE:0760

---

### Post by avlinux on 2009-11-06
Any suggestions?  I'm guessing its just not compatible, regardless if I'm using the ndiswrapper utility.

---

