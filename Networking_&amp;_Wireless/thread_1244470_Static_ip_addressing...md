---
title: "Static ip addressing.."
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by karthick87 on 2009-08-19
I am using two NIC cards,eth0 is assigned as dhcp and eth1 is set to be static..But after a restart eth1 is automatically set to be dhcp..How to solve it? What may be the problem?

---

### Post by Sam Lars on 2009-08-19
Could you post what you have in your /etc/network/interfaces file?

---

### Post by karthick87 on 2009-08-20
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet dhcp

---

### Post by Sam Lars on 2009-08-20
Were you using the Network Settings window to configure it?
You could try setting it up in that file instead. The part with eth0 looks fine, but you don't have anything in there for eth1.
[http://codesnippets.joyent.com/posts/show/319](http://codesnippets.joyent.com/posts/show/319)

---

### Post by karthick87 on 2009-08-20
S for eth1 nothing found i have tried restarting my networking service etc but even though i couln't find anything for  eth1..How to fix it?

---

### Post by Sam Lars on 2009-08-20
Did you change your /etc/network/interfaces?

---

### Post by Iowan on 2009-08-20
Something to try that probably won't work... but is easy to undo.
Add the following line to */etc/network/interfaces*:```
iface eth1 inet manual
```

---

