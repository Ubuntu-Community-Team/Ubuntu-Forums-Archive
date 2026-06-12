---
title: "Port 22 already used on many Routers . i can't use SSH"
date: 2010-02-22
forum: Networking &amp; Wireless
---

### Post by s.l.i.m on 2010-02-22
Hi,

The port 22 is already used in my router. I can't forward it to my desktop-computer. I changed the port of my SSH Server to 2222. It works on local but when i try with the external ip it doesn't work.

i try the command : ssh -p 2222 externalipadresse

i'm using OpenSSH Server and OpenSSH Client on ubuntu karmic 9.10.

Thanks.

---

### Post by maweki on 2010-02-22
Have you configured your router to forward all packets from that port to the machine in question? You could also set your computer up as DMZ (if your router supports this).

The Router does not know where to forward packages to, if you do not tell him explicitly.

---

### Post by Sin@Sin-Sacrifice on 2010-02-22
It's probably your ISP blocking that port. Contact them and see what ports they have open for you to use or you can use nmap to figure it out if you don't like calling. I had the same problem with remote desktop and ftp with time warner.

---

### Post by Neezer on 2010-02-22
> **s.l.i.m said:**
> Hi,

The port 22 is already used in my router. I can't forward it to my desktop-computer. I changed the port of my SSH Server to 2222. It works on local but when i try with the external ip it doesn't work.

i try the command : ssh -p 2222 externalipadresse

i'm using OpenSSH Server and OpenSSH Client on ubuntu karmic 9.10.

Thanks.

You also need to make sure that the client knows to send the request to port 2222. It is in the config file. I am also using port 2222 for my ssh needs. Good Luck

---

