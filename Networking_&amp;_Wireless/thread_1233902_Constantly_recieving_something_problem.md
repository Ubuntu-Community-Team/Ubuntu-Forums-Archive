---
title: "Constantly recieving something problem"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by Pitboss on 2009-08-07
Hi. I'm a total newbie so I'll appreciate any help. In the gnome-system-monitor I noticed something strange. I'm constantly receiving something from the web but I'm not sure what it is, and I don't know how to locate the program that does this. I'm receiving something in speed from 10K~100K. So any ideas?

---

### Post by Kraut~salat on 2009-08-07
netstat will list all the open sockets of you system, including network sockets. read the man pages (type "man netstat" in a console). "netstat -p tcp udp" will show you all the open tcp und udp connections

---

### Post by Pitboss on 2009-08-07
Thanks, I tried netstat before, the problem was I can't actually see what amount of information is transfered via a particular connection.

---

### Post by superprash2003 on 2009-08-07
you could use firestarter , it has an active connections window , which shows source and destination , i think its more or less same as the netstat output

---

