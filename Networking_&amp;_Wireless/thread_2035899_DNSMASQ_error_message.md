---
title: "DNSMASQ error message"
date: 2012-07-31
forum: Networking &amp; Wireless
---

### Post by M4DM4DZ on 2012-07-31
Hey guys,

Im running a web server on a local intranet using apache2, Im also running dnsmasq on the same machine.

I've edited the following line in  /etc/dnsmasq.conf as follows

```
address=/com/192.168.2.1
```This directs all ".com" traffic to my local web server, problem is my webservers address is actually 192.168.2.1/webserver

if i insert the full path (address=/com/192.168.2.1/webserver) i get a "Failed" message when starting dnsmasq.

I've tryed adding quotation marks, brackets, everything!

```
[FAIL] Restarting DNS forwarder and DHCP server: configuration syntax check failed!
```Can anyone help me, im sure this is pretty simple.... I've already read the dnsmasq manual, nothing seems to stand out....

---

