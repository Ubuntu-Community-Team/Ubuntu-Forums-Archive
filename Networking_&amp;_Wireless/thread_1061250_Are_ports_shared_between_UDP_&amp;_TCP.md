---
title: "Are ports shared between UDP &amp; TCP?"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by bluedalmatian on 2009-02-05
This may sound a silly question and I apologise but if something is using TCP port 1000 say, would that prevent another program using UDP port 1000?

In other words, does IP & port & transport protocol determine the endpoint or just IP& port

Thanks

---

### Post by redmk2 on 2009-02-05
Interesting question.  What do you mean by endpoint?  

See:
[[COLOR="Green"]**OSI Networking model**[/COLOR]]("http://www.laynetworks.com/osi.htm")

and
[[COLOR="Blue"]**TCP/UDP Ports**[/COLOR]]("http://www.bleepingcomputer.com/tutorials/tutorial38.html")

Edit: TCP ports are different than UDP ports.  They are values in the header of the data packet

---

### Post by fwre01 on 2009-02-05
hi bluedalmatian, those two links above are good reads, and well worth a look for a more comprehensive understanding of TCP/IP. In short the answer is NO, running a 'socket' (as it's refered to) on tcp port 1000 will have NO affect if you are also running a socket on UDP 1000.

---

### Post by albinootje on 2009-02-05
> **bluedalmatian said:**
> This may sound a silly question and I apologise but if something is using TCP port 1000 say, would that prevent another program using UDP port 1000?

If you look at /etc/services you can see that some protocols only use tcp, or only udp.
When a program only uses tcp, then it should be possible to run another program on the same port using udp afaik.

---

### Post by redmk2 on 2009-02-05
> ...then it should be possible to run another program on the same port using udp afaik.

albinootje.

They are NOT the same port.  As I said they are not a physical thing.  They are values in a packet header.  The values are NOT the same, hence not the same port (socket).  As an aside TCP/UDP sockets are not the same as UNIX sockets either.

---

