---
title: "Somehow port 80 is being blocked."
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by pepsifx357 on 2010-04-27
So I set up an Ubuntu 10.04 server with apache2 installed, but for some reason I can't get to it from my browser.  the iptables have all changed directories in 10.04 so I can't find the iptables.  Apparmor wasn't the problem.  The network hard ware is not the problem.  There is something inside of 10.04 that is blocking port 80.  I can ping it all day using the ip address but when I ping it useing [http://ipaddress](http://ipaddress) it can't find the host. Anyone know what's up with that?

---

### Post by Iowan on 2010-04-27
[This]("https://help.ubuntu.com/community/ApacheMySQLPHP#Securing%20Apache") document is being merged with [Ubuntu Server Guide]("https://help.ubuntu.com/9.10/serverguide/C/index.html"), but might still be useful. (It's also pre-Lucid...)

---

### Post by wojox on 2010-04-27
> **pepsifx357 said:**
>  I can ping it all day using the ip address but when I ping it useing [http://ipaddress](http://ipaddress) it can't find the host. Anyone know what's up with that?

You don't use http:// to ping a computer. Just the domain name ( [www.google.com](www.google.com)) or ip address

---

### Post by pcrat on 2010-04-27
most isps block incoming http connections on port 80. use an alternate port like 8080 or 1010 or whatever. thats what i do. then i use co.cc for my [www.com](www.com) domain name and use zoneedit.com for my forwardering.. all free no ads on your pages at all.

---

### Post by pepsifx357 on 2010-04-28
> **pcrat said:**
> most isps block incoming http connections on port 80. use an alternate port like 8080 or 1010 or whatever. thats what i do. then i use co.cc for my [www.com](www.com) domain name and use zoneedit.com for my forwardering.. all free no ads on your pages at all.

The server is sitting right next to me.

Turns out it wasn't Ubuntu, It was WINDOWS 7!!! aARGHH

Yeah, just stick with XP if you a windows person.  However I still can't get windows to go to the website no matter what.  I've cut off the firewall, I don't own or would ever use norton, zone alarm, or mcafee, They're connected via unmanaged switch, I deleted internet history, and used both IE and fire fox.  The funny thing is, my ubuntu virtual machine that is running on windows can get to the site but windows can't, talk about wierd.

---

