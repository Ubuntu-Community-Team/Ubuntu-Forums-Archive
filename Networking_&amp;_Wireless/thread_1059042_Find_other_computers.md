---
title: "Find other computers"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by detroit/zero on 2009-02-03
Is there a way to get a list of computers and their ip addresses on a local network without pinging every possible address? 

I mean, issue a command and have it spit out  list of hostnames and addresses?

---

### Post by nixscripter on 2009-02-03
Not unless they're all running a protocol daemon, like [zeroconf]("http://en.wikipedia.org/wiki/Zeroconf").

---

### Post by detroit/zero on 2009-02-04
> **nixscripter said:**
> Not unless they're all running a protocol daemon, like [zeroconf]("http://en.wikipedia.org/wiki/Zeroconf").
lies.

nmap does it.

---

### Post by nixscripter on 2009-02-04
Hmm. Maybe it uses NetBIOS names or something. What command did you run to do that?

---

### Post by detroit/zero on 2009-02-04
```
 nmap -O 192.168.1.0-255
```

i pulled that out of my history.. the -O is OS detection, but using nmap without the -O switch will accomplish the same task, just without os descriptors.

i wasn't posting a trick question, btw, i just never used nmap before and didnt know it existed. i just ran across it in my searches..

---

### Post by nixscripter on 2009-02-04
Oh, you just wanted their IPs. I meant you couldn't get their **hostnames** without zeroconf.

---

### Post by cariboo on 2009-02-04
I use a script I found :

```
sudo nmap -PR -sP 192.168.1.0/24
```

It usually finds all of the network devices. I have an SMC Barricade that i use for a wireless access point, that doesn't show up every time.

Jim

---

### Post by detroit/zero on 2009-02-05
> **cariboo907 said:**
> I use a script I found :

```
sudo nmap -PR -sP 192.168.1.0/24
```It usually finds all of the network devices. I have an SMC Barricade that i use for a wireless access point, that doesn't show up every time.

Jim
Works like a charm.. hostnames, macs, ip's, the whole shabang.


Gracias!

---

