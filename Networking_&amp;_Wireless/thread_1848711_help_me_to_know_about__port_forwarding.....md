---
title: "help me to know about  port forwarding...."
date: 2011-09-23
forum: Networking &amp; Wireless
---

### Post by jpjohnj on 2011-09-23
hi..

as per my knowledge, port forwarding is a process which help to forward the blocked port in the network/internet to the end user...

i need to know....

1.how to find the blocked port on the network?

---

### Post by Lisiano on 2011-09-23
All applications that act as servers (The ones that need port-forwarding) usually tell you what port it is.

Also here is a list of default TCP and UDP ports in case the program for some reason doesn't tell it.
[http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)

Or if you prefer, you can use netstat.
For TCP
```
netstat -t
```
For UDP
```
netstat -t
```

---

### Post by i.r.id10t on 2011-09-23
> **Lisiano said:**
> All applications that act as servers (The ones that need port-forwarding) usually tell you what port it is.

Also here is a list of default TCP and UDP ports in case the program for some reason doesn't tell it.
[http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)

Or if you prefer, you can use netstat.
For TCP
```
netstat -t
```
For UDP
```
netstat -t
```

Or just netstat -l4 -n

---

### Post by Iowan on 2011-09-23
Port forwarding can also be a "redirect". Your router probably has no web server, so port 80 wouldn't mean much to it. A port forward would send the port 80 traffic to another machine which DOES know what to do with it (ie., it has a web server).

What/where do you need to forward traffic?

---

