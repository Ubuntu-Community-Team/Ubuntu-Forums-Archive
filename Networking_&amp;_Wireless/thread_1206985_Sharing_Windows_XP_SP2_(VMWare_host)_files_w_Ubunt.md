---
title: "Sharing Windows XP SP2 (VMWare host) files w Ubuntu 8.10 LTS Desktp (VMWare guest OS)"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by Zorrorrorro on 2009-07-07
Hi there,

I want to share files on my XP host OS with my Ubuntu VMWare Guest OS using Workstation 6.5.2. How do I go about doing this? 

Thanks!

Zorrorrorro

---

### Post by Zorrorrorro on 2009-07-07
Sorry, I meant 8.04 LTS Hardy Heron, not 8.10

---

### Post by sedawk on 2009-07-07
There should not be any difference to a setup with real
Ubuntu PCs. As long as you have setup networking, so
you VMware guests have a virtual network interface you can
test that the basic networking works (e.g. ping the IP
of your VMWare host. This is the normal IP when using bridged
network or a new "private" one when using NAT or host-only networking).
If that works try to test basic functionality of the share using
command line tool "smbclient" or try Menu->Places->Connect to Server.

---

