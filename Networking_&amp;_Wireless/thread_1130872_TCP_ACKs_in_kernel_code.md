---
title: "TCP ACKs in kernel code"
date: 2009-04-20
forum: Networking &amp; Wireless
---

### Post by rrbarbosa on 2009-04-20
Hi,

I'm interested in understanding the linux kernel implementation for TCP. Does anyone know a good reference?

Particularly what interests me is how ACKs are produced. I need to understand situations that trigger quickacks (like on slow start, retransmissions, etc.) and delayed acks. I also need understand what can cause the transmission of an ACK that acknowledge more than two packets.

So far the best reference I found is:
[http://myhsc.pbwiki.com/Inside_Linux_TCP::Delayed_Ack](http://myhsc.pbwiki.com/Inside_Linux_TCP::Delayed_Ack)

But still there are parts that I don't complete understand. And by "good reference" a specialized forum is a possibility (i guess ubuntu forum is not the best place to look for this info).

Thanks,
Rafael

---

### Post by lloyd_b on 2009-04-20
Take a look at ["TCP/IP Illustrated, Vol 1"]("http://www.uic.rsu.ru/doc/inet/tcp_stevens/") - This is probably the *best* reference for TCP/IP ever written (I'd suggest picking up the hardcopy version is your budget can afford it, but the HTML above should get you started).

Note that this info isn't Linux specific, but you'll have a hard time finding *any* *nix operating system that doesn't follow the same rules.

Lloyd B.

---

### Post by rrbarbosa on 2009-04-20
Yeah, definitely this book is great. But I would not say that every nix implementation follow exactly what is there. 

For instance, I believe one of the topics I am interested, the 'quickacks' implemented on linx (at least on kernel 2.6) that makes the congestion window to grow faster on the 'slow-start' phase is not addressed on this book. What I really need is info. on the internals of the linux kernel implementation. 

Rafael

---

### Post by regala on 2009-04-20
> **rrbarbosa said:**
> What I really need is info. on the internals of the linux kernel implementation.

Well, you have the sources :)
I suggest net/ipv4/tcp.c and net/ipv4/tcp_*.c for all the TCP congestion algorithms.

---

### Post by rrbarbosa on 2009-04-21
> **regala said:**
> Well, you have the sources :)
I suggest net/ipv4/tcp.c and net/ipv4/tcp_*.c for all the TCP congestion algorithms.

Sure I have the code. I am trying to understand it but is hard work. That's why I am still looking a good reference. Any other tips?

---

