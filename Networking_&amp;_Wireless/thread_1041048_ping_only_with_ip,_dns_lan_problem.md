---
title: "ping only with ip, dns lan problem?"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by mael15 on 2009-01-16
hi folks,

i feel like i am missing something very simple. i have been googleing this problem a lot.

i have a notebook with ubuntu 8.10 in a lan with a router as dns server. i want to connect to a winxp computer named "server" through it's name, not ip. since the router uses dhcp and i am in a company, i cannot switch to fixed ips.

these are the temporary adresses
laptop: 192.168.1.33
router: 192.168.1.1
server: 192.168.1.34

i can ping 192.168.1.34 successfully, but ping server fails. internet works fine though.

what can i do to access server through it's name, not ip?
thanx!

---

### Post by mael15 on 2009-01-19
has noone any idea?!

---

### Post by Iowan on 2009-01-19
/etc/resolv/conf shows the notebook is using the router for DNS?

---

### Post by mael15 on 2009-01-19
thanx iowan,
the problem was solved by adding wins in the etc/nsswitch.conf:
[http://www.sigmundvoid.com/2007/08/netbios-names-and-ubuntu/](http://www.sigmundvoid.com/2007/08/netbios-names-and-ubuntu/)
\\:D/

---

### Post by Iowan on 2009-01-19
Glad you got it solved. I'll bookmark your link - that problem pops up frequently.

---

