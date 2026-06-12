---
title: "name resolution issue"
date: 2009-10-22
forum: Networking &amp; Wireless
---

### Post by eko291 on 2009-10-22
I have a very strange issue on my network, with name resolution. I am trying to hit my website URL (being hosted on an Ubuntu Server VM on my a machine on my network) and the name is getting resolved to another computer on my network. The name seems to resolve to the machine acting as the host for the virtual machine. 

I have no idea what to check to see why the resolution is happening this way. If anyone has hints, I welcome them!

---

### Post by eko291 on 2009-10-22
I don't know that this is the reason, but I resolved the issue by setting the hostname in my /etc/hosts file.

---

