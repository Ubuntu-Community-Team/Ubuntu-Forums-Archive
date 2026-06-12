---
title: "choose gateway before using web browser"
date: 2010-06-19
forum: Networking &amp; Wireless
---

### Post by boondocks on 2010-06-19
This Ubuntu desktop has 3 network interfaces:
[LIST=1]
[*]LAN eth0: ip address 192.168.3.6  gateway **192.168.3.1**
[*]VPN tun1: ip address 192.168.7.4  gateway **192.168.7.1**
[*]VPN tun2: ip address 192.168.9.2  gateway **192.168.9.1**
[/LIST]

For Chrome or Firefox, by default the 192.168.3.1 gateway is used.

How do I change this such that:
[LIST]
[*]I can manually choose the 192.168.9.1 or 192.168.7.1 or 192.168.3.1 gateway.
[*]From the command line.
[*]Before running Firefox/Chrome.
[*]Without re-configuring any network interfaces.
[*]So that ONLY Firefox and Chrome browsers are affected.
[*]There is no impact on any other applications.
[/LIST]

---

### Post by boondocks on 2010-06-19
For example, in bash when I do:
```
export http_proxy="http://192.168.4.1:8080"
wget http://checkip.dyndns.org/
```

This uses the proxy at the 192.168.4.1 server.
So the wget request is returns the WAN ip address of the 192.168.4.1 server.

I want to so something similar and choose from:
192.168.3.1
192.168.7.1
192.168.9.1

But I cannot use "export http_proxy..." because there are no proxy servers running on these 3 gateways.

---

