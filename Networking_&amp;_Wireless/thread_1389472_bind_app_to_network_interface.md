---
title: "bind app to network interface"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by marinero_arrr on 2010-01-24
Hello,
I have a problem configuring vuze with multiple internet conections(multiple ISPs). 
vuze has an option to do this (bind to local ip address), I specify the interface to bind it to but I can't get it working, the torrents don't download.

I run the network test inside vuze and the test connect with my network default interface

my default interface is
10.0.0.2 (with internet)
eth1 (connected to another ISP)
192.168.0.222

both have the 30000 port open (this is the por configured in vuze)

I'd tried all the options in "bind to local ip address" box in vuze
eth1
eth1[1] (the ipv4 of that interface)
eth0,eth1 (can't do network balance neither)


Can someone help me with vuze or wrap an aplication somehow to bind it to a network interface (I prefer transmission but has no options to bind)

I think you can arrange something with iptables to send all the traffic in a port to another interface than default but I don't know iptables

any workaround?

thanks

---

