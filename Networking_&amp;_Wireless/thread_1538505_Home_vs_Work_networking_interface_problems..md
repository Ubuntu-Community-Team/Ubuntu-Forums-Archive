---
title: "Home vs Work networking interface problems."
date: 2010-07-25
forum: Networking &amp; Wireless
---

### Post by grandsatrap on 2010-07-25
I want my laptop to be able to connect to the internet both at home and at work. The problem is that there are two different types of networks and I have to keep manually configuring my network connections. It should automatic as I am using two different interfaces.

HOME: 
connect using wireless (eth1)
static IP address: 192.168.1.3 
gateway: 192.168.1.1
no proxy


WORK:
connect using ethernet cable (eth0)
dynamic IP address (e.g. 10.10.1.123)
proxy server: 10.10.0.100 port 8888

I have tried messing with /etc/network and ifconfig and a bunch of stuff. I can't get it working. The proxy is part of the problem. The network settings should take care of the proxy, then Firefox can just use the system proxy settings. Also the http_proxy environment variable should be set properly too. I don't want to have to do [export http_proxy=""] everytime I bring my laptop home.  I realize that some running processes (e.g. conky weather) will not be able to make the switch seamlessly as they probably have a cached copy of the http_proxy variable. I can just restart conky.

---

