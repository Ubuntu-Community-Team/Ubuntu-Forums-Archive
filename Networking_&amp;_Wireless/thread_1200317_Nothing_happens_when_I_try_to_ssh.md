---
title: "Nothing happens when I try to ssh"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by josephellengar on 2009-06-29
So, I have port forwarding in effect.  My firewall allows port 22.  The command that I am using is:

ssh -X -C -l ross xx.xxx.xxx.xx
I also tried: sudo ssh xx.xxx.xxx.xx

Whenever I do one of those commands *nothing* happens.  The connection just times out.  My computer is definitely connected to the internet.  Any advice?

---

### Post by superprash2003 on 2009-06-30
use this online port scanner to see if the port is open [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by wirelessmonkey on 2009-06-30
Can each machine ping the other?

---

### Post by josephellengar on 2009-06-30
> **wirelessmonkey said:**
> Can each machine ping the other?

yes. no dropped packets.  One detail that I forgot to mention is that they both have the same ip address, if that matters.  But I do have port forwarding to a specific local computer.

---

### Post by Iowan on 2009-06-30
> **idigchess said:**
> One detail that I forgot to mention is that they both have the same ip address, if that matters.  It matters... Networks generally do not work well with more than one machine claiming a specific IP address.

---

### Post by wirelessmonkey on 2009-07-01
Yes, it matters. If attempting to ping an IP that is assigned to the local machine, it doesn't need to move any farther than the loopback interface.... your ssh request is not being forwarded.

---

### Post by Iowan on 2009-07-01
Although "we" hinted at it, neither of actually suggested that you should try changing the IP address of one of the machines.  The "client" might be easier - otherwise, you will need to change the port-forwarding in the router.  BTW, if both machines are on the same side of the router, port-forwarding will not come into play.  That will only be necessary if you want to access the "server" from outside the network (via internet?).

---

### Post by Geoff918 on 2009-07-01
This is really basic, but have you tried SSH from the machine itself to itself? (local loopback) to see if the SSH service is running and accepting connections? Before the myriad other issues may come into play with port forwarding, etc. is the service itself operational and responsive?

---

### Post by josephellengar on 2009-07-01
> **Iowan said:**
> Although "we" hinted at it, neither of actually suggested that you should try changing the IP address of one of the machines.  The "client" might be easier - otherwise, you will need to change the port-forwarding in the router.  BTW, if both machines are on the same side of the router, port-forwarding will not come into play.  That will only be necessary if you want to access the "server" from outside the network (via internet?).

So does that mean that ssh would work with a local ip address, if I don't try to use the web ip  address?

---

### Post by josephellengar on 2009-07-01
> **Geoff918 said:**
> This is really basic, but have you tried SSH from the machine itself to itself? (local loopback) to see if the SSH service is running and accepting connections? Before the myriad other issues may come into play with port forwarding, etc. is the service itself operational and responsive?

No, I haven't.  Duh :oops:

---

### Post by Iowan on 2009-07-01
IF the SSH server is running (you could also check from a terminal with **ps -ef |grep ssh**) and if the client machine is on the same side of the router (same subnet?), you *should* be able to connect with: ```
ssh username@serverIPaddress
```... at least, that's how I access the servers on my network.

---

### Post by josephellengar on 2009-07-01
OK, thanks everybody!  This should be enough for me to figure it out.  I think that I've ironed much of the problem.  I'll just message back here if I have another problem.

---

### Post by wirelessmonkey on 2009-07-02
Iowan, that was a good point, and sadly a far too common mistake in basic troubleshooting. Thank you for pointing it out!

---

