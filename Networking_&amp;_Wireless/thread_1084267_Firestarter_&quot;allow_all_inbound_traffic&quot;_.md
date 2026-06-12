---
title: "Firestarter &quot;allow all inbound traffic&quot; policy"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by carlbastos on 2009-03-01
Hi there, I've installed 8.10 amd64 version recently and I'm using the iptables GUI interface (firestarter) to share my internet through a wired connection. 

Ok, everything was nice, shiny and happy...

The problem is that I run some servers with random ports and firestarter doesn't have an "allow all" policy for the inbound traffic, I can only specify some IP's, but I can't make a rule for every IP that connects to my servers and I can't make a rule to allow a specific port, because I use them randomly.

Is there a way to make firestarter ONLY share the internet?
(w/out blocking the incoming traffic from all the ports)

something like an allow rule with this IP "*.*.*.*" to allow all, or whatever...

thanks in advance.

---

### Post by carlbastos on 2009-03-02
ne1?

---

### Post by doublehelixer on 2011-01-07
I know this thread is old, but somebody might find this useful -- you need to make a rule for "Allow connections for host" using CIDR notation for *any *IP address:
0.0.0.0/0

---

### Post by scrooge_74 on 2011-05-04
Old, but still valid. My provider is down, I had to improvise using one of those USB 3G dongles, and only a Debian Squeeze wanted to detect it, so I had to install Firestarter to share conection. Then VoIP phone could not get through to provider server.

So doublehelixer solution came through for me.

---

