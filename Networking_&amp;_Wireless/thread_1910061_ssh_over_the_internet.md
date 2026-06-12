---
title: "ssh over the internet"
date: 2012-01-16
forum: Networking &amp; Wireless
---

### Post by VVAW on 2012-01-16
I would like to access my ubuntu machine via ssh over the internet.
Is there instruction on how this is done.

I have openssh intstalled and working on the Lan.
I have registered on no-ip

---

### Post by jsra on 2012-01-16
Hi,
is your ssh server behind a router? If it is then you have to forward ssh port to your server on router. You didnt say what exactly is your problem; for connecting to ssh you can use [putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html").

---

### Post by VVAW on 2012-01-16
Yes I am using putty... So I put in the router portforwarding 
on port 22 to internal local ip what would be the external port and do i need source address

---

### Post by jsra on 2012-01-16
You dont need to specify source IP address, you can just forward all requests to specific port. Easiest way is to forward external tcp port 22 to internal IP tcp port 22, if your ssh is running on default port 22.
Then you just have to connect from internet to your external router IP on port 22 with ssh protocol.
If you have some troubles with settings of your router you can check this site, there are guides for many services and routers, including ssh:
[http://www.portforward.com]("http://www.portforward.com")
[http://portforward.com/english/applications/port_forwarding/SSH/SSHindex.htm]("http://portforward.com/english/applications/port_forwarding/SSH/SSHindex.htm")

---

### Post by jonobr on 2012-01-16
Hello

If you open a terminal window

(just type terminal in search bar)
and run

```
sudo tcpdump -i any port 22
```

let the thing sit there monitoring.

Ssh from outside.
If no packets appear then your either being blocked on 22 by the ISP or your forwarding isnt working

---

