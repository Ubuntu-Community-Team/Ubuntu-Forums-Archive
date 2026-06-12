---
title: "Ubuntu asks my router for Ports via UPnP"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by kaefert66014235 on 2008-12-13
Hi there!

I've got 2 notebooks running on Ubuntu, which both ask my router for ports via UPnP.
The one running Ubuntu 8.10 askes for the port 27113 for both UDP & TCP.
The other one running Ubuntu 8.04 askes for the port 3082.

I found out that the port 3082 seems to have something to do with wireshark, which is installed on the Ubuntu 8.04 machine, but it is not running (none of the names of the processes running sounds like it) and it has not been started for a few months..

I couldn't find any information on the port 27113.

If someone knows what reasons this could have, please tell me so. Thanks.

---

### Post by superprash2003 on 2008-12-13
you dont need to open them if you dont use them,..

---

### Post by kaefert66014235 on 2008-12-13
> **superprash2003 said:**
> you dont need to open them if you dont use them,..

my problem is that i do require to use UPnP for other applications that i want to be able to automatically request portforwarding from my router.

but these 2 ports get requested from my router by these 2 ubuntu machines and i dont know why or by which application.

I would need some guidance how to find out which applications did request these ports to get forwarded to the ubuntu machines


EDIT: I now have a 3rd Ubuntu laptop in my network which is a fresh install of Ubuntu 8.10 and that one also requested the portforwarding of a port: 30774. I've not installed any additional software on this 3rd laptop. This means this is a general issue for Ubuntu.

---

