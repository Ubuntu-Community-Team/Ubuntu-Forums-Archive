---
title: "using different hosts file on different networks"
date: 2009-06-30
forum: Networking &amp; Wireless
---

### Post by Lumme on 2009-06-30
Hi guys.
I'm trying to make my life a little less complicated.
I have recently build my own mailserver, and things are running smoothly.
Only one problem left.
I would like to use thunderbird (or another mailclient) to connect to the server from my laptop, without having to change settings everytime i leave my home.

The server is on my private lan, so from home i have to add an entry i /etc/hosts like this : 10.0.0.10 mail.server.com.
But when i'm anywhere else this of course would prevent connection.

Any ideas. (and not something like creating two accounts in thunderbird)

---

### Post by jhannah on 2009-06-30
I think the easiest solution is just to update your hosts file (or comment out the line you use to connect when at home if it is a valid FQDN). Beyond that, provided it is a valid FQDN, you would likely need to run a name server on your home network which hands out the RFC1918 IP you are using on the server for that domain but that seems much more complicated than it is worth unless learning how to run a name server is something you are interested in learning.

---

### Post by Lumme on 2009-07-01
Thank you for replying.

Maybe I'm just in it over my head, but what I was hoping for was something in the line of the proprietary network managers for windows. Where you can switch "network location", and load a set of preconfigured settings (hosts, dns etc.)

Perhaps Gnome NetworkManager will include this in the future :)

---

