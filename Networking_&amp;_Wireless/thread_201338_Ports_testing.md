---
title: "Ports testing?"
date: 2006-06-21
forum: Networking &amp; Wireless
---

### Post by beerloko on 2006-06-21
How do I check if my ports is open?

[]'s

Thank's


Bruno.

---

### Post by jvl on 2006-06-21
netstat -utln

u= udp sockets t= tcp sockets l=listening status n=don't resolve service names i.e. show just port numbers.

You may add 'p' and run it as root to see which processes have opened the sockets like this:
netstat -utlnp

---

### Post by jvl on 2006-06-21
nmap scan from another computer might help as well.

---

### Post by beerloko on 2006-06-21
[QUOTE=jvl]netstat -utln

u= udp sockets t= tcp sockets l=listening status n=don't resolve service names i.e. show just port numbers.

You may add 'p' and run it as root to see which processes have opened the sockets like this:
netstat -utlnp[/QUOTE]

I need any application that check all ports for verify it has external access as port dectetive for windows.


Thank's

---

### Post by jvl on 2006-06-21
nmap from another computer is a way to go then. [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/)

you could look at the Shields UP! at Gibson Research ([https://www.grc.com/)](https://www.grc.com/)), but it scans only first 1056 ports.

---

