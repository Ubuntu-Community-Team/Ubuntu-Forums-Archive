---
title: "Problem: Add persistent route"
date: 2011-10-04
forum: Networking &amp; Wireless
---

### Post by ownilink on 2011-10-04
Hi all,

Lately I've been starting to use Ubuntu (11.04). I love it! I'm still a beginner, but I learn more with time. 
I want to add some persistent routes in /etc/network/interfaces.
I've been looking on the internet and on the forum but i cant seem to get it work.

If I type "sudo route add -net 192.168.30.2 gw 172.21.1.1 netmask 255.255.255.255" in a terminal the route gets added fine. But ofc this route is not persistent.

This is how my interfaces file looks(how i think that it should work):

auto lo
iface lo inet loopback
up route add -net 192.168.30.2 gw 172.21.1.1 netmask 255.255.255.255

After, I use the sudo /etc/init.d/networking restart and i get this:

/etc/network$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

But if i use the "route" command after it doesnt show my route.

Any help will be appreciated.

Thanks,

Ferenc

---

### Post by jonobr on 2011-10-04
Hello

Im not sure if your example is what your exactly using but your netmask should probably (im guessing ) be a class C,
255.255.255.0


```
route add -host 20.20.20.20 netmask 255.255.255.0 gw 192.168.1.1 dev eth0

```


[Here]("http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html") is a good writeup with explanation on testing

---

