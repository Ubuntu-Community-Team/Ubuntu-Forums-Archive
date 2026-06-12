---
title: "Port Forward localhost:80 to localhost:8080"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by telseth on 2009-12-25
I have a VirtualBox machine set up and have forwarded the IIS install on the virtual machine's port 80 to my local port 8080.  I need to forward the hosts 8080 to the host's port 80.

I have set up iptables to allow this from the external network, [http://myexternalip/](http://myexternalip/) works from another computer, but [http://localhost/](http://localhost/) from the host computer fails.  

How can I get this to work?

VirtualBox:80 -> LocalHost:8080 -> LocalHost:80

---

