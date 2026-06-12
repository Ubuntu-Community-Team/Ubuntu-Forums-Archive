---
title: "How to access files on linux server remotely"
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by shakyn on 2010-03-27
Hello,

I have a Linux server and a static IP address. I want to access data on my server remotely using this IP address. How do I do it? I have don some research and have a very basic idea. Pleas help!

Thanks!

---

### Post by pbpersson on 2010-03-27
How are you sharing the files on the Linux server?  Are you using Samba?  

What sort of system are you using to access the files?  Another Linux machine?

In theory once you have Samba configured on the sharing machine you would install and use a Samba browser on the desktop machine to connect to the server and access the files.

---

### Post by jmr423 on 2010-03-27
I installed proftpd on my ubuntu server 9.10 and it works amazingly. the command to install it on ubuntu server9.1 is 

```
sudo apt-get install proftpd
```

I would say this is definitly woth looking into.

---

### Post by Cabalbl4 on 2010-03-27
I would recommend to install webmin. It can configure proftpd via simple GUI and  allows to edit all desktop (and samba) settings and many things more remotely.

BTW I set it to listen to localhost only. It provides me a usable GUI for proftpd and firewall.

---

