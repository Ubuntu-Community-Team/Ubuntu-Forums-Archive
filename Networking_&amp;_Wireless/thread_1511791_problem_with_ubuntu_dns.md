---
title: "problem with ubuntu dns"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by rd1381 on 2010-06-17
recently i have many problem with ubuntu networking

till last night i could access nvidia site. but today (maybe after some updates) i cant . it stays in looking up state in firefox.

i thought it was my isp so i changed nameservers in /etc/resolve.conf and tried "sudo /etc/init.d/networking restart" but that disabled dns altogether. i mean i couldnt even access google.funny thing is if i logoff  and login again(no restarting the pc) it gets fixed( not the nvidia part though).

and wierd thing is when i "sudo /etc/init.d/networking restart" and i cant  connect in ubuntu to anything , i still can run vmware and virtualize windows and from inside that i can browse internet ( even nvidia site) without any problem.

any ideas?

---

### Post by jonobr on 2010-06-17
It sounds like two different issues,
It sounds as if stopping the networking and restarting is not working.
On the DNS issue for nvidia itself,
what happens when you do a ping to nvidia?
Do you get the right Ip address?

I believe there is a redirect from that address and that may be the issue on your end of the browser, however, I reckon checking resolution from a terminal window first would be a good start.

---

### Post by rd1381 on 2010-06-17
> **jonobr said:**
> It sounds like two different issues,
It sounds as if stopping the networking and restarting is not working.
On the DNS issue for nvidia itself,
what happens when you do a ping to nvidia?
Do you get the right Ip address?

I believe there is a redirect from that address and that may be the issue on your end of the browser, however, I reckon checking resolution from a terminal window first would be a good start.

you are right. plz forget nvidia issue,it can be from my isp.

but i still have my other problem.
how can i find what is the issue?

---

### Post by Iowan on 2010-06-18
I've seen mixed results of using **sudo service networking restart.** Dunno if it matters that [this]("http://ubuntuforums.org/showthread.php?t=1489373") one was lubuntu...

---

