---
title: "Two networks in single nic"
date: 2013-01-04
forum: Networking &amp; Wireless
---

### Post by yogix on 2013-01-04
I'm having only one ethernet port in the server in my lab and server has to be setup for two networks. One network is for thin clients and the other for Internet. The thin clients gateway is 192.168.0.1 and Internet gateway is 192.168.1.1. Right now, I've setup two wired connections, one for Internet access and other for Thin clients. But only one can be used at once, not both. Is it possible for me to connect to both the networks in server at same time.? The problem is, I cannot use thin clients when connected to Internet and cannot use Internet when the server is connected to thin clients.
I tried creating virtual ip(eth0:0) for existing eth0, but it didn't work. Pls help me.
I'm using Ubuntu 10.04.

Thanks in advance.

---

### Post by chadk5utc on 2013-01-04
> **yogix said:**
> I'm having only one ethernet port in the server in my lab and server has to be setup for two networks. One network is for thin clients and the other for Internet. The thin clients gateway is 192.168.0.1 and Internet gateway is 192.168.1.1. Right now, I've setup two wired connections, one for Internet access and other for Thin clients. But only one can be used at once, not both. Is it possible for me to connect to both the networks in server at same time.? The problem is, I cannot use thin clients when connected to Internet and cannot use Internet when the server is connected to thin clients.
I tried creating virtual ip(eth0:0) for existing eth0, but it didn't work. Pls help me.
I'm using Ubuntu 10.04.

Thanks in advance.
In terminal type and post the results
> sudo ifconfig

Yes it is possible to stack multiple ip's to a single nic usually done with local network and vpns
Heres a good link for adding additional ips to your nic
[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)
Scroll down the page and look for" Setting up Second IP address or Virtual IP address in Ubuntu "

---

