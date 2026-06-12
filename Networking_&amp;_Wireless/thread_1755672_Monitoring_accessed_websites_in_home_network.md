---
title: "Monitoring accessed websites in home network"
date: 2011-05-11
forum: Networking &amp; Wireless
---

### Post by nielsteekens on 2011-05-11
Hi,
I want to monitor the websites that people in my network are visiting.
It's a home network with various devices (PCs, phones, Ipads), and a ubuntu headless server. I'd like to install some monitoring software on the server, which would ideally provide me a list of website the devices (attempted to) connected to.
Does such a software exists?? Can I control it via Webmin. Would setting my NIC in promiscuous mode affect performance??
Thanks

---

### Post by Lars Noodén on 2011-05-11
If you set up squid or varnish as a transparent proxy you can do that.  

Just be sure not to violate any privacy expectations, ethics or laws in doing so.

---

