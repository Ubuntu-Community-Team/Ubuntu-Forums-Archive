---
title: "resolv.conf keeps getting reset by something"
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by jontsai on 2011-08-26
Hello,

I need help figuring out why my resolv.conf keeps changing to this, causing me to not be able to access the outside internet and only the local network:

$ cat /etc/resolv.conf
nameserver 192.168.16.1
domain localdomain
search localdomain

I thought I fixed it by getting rid of the loopback interface and adding in the eth0 interface in /etc/network/interfaces ([http://jontsai.posterous.com/howto-debianubuntu-fix-resolvconf-and-network](http://jontsai.posterous.com/howto-debianubuntu-fix-resolvconf-and-network))

I've tried things like doing:
$ sudo ifconfig eth0 down
$ sudo ifconfig eth0 up
$ sudo /etc/init.d/networking restart
$ sudo dhclient

And then things would work temporarily, and eventually the nameserver in resolv.conf would get reverted again.

Any thoughts?

---

### Post by Actonix on 2011-08-26
Being relatively new to Ubuntu I might not be able to help unless in the absence of any other assistance you are prepared to experiment

... but before that happens along do you mind my asking if you have implemented any security in your installation.

---

