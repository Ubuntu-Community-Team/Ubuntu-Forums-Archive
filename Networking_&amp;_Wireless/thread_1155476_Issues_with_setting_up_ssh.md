---
title: "Issues with setting up ssh"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by Glaciusor on 2009-05-10
I am running Ubuntu 9.04 on an old server I obtained recently that my college was getting rid of (they are switching to Vista and this machine can't handle it, so I saved it from recycling). I tried getting openssh installed and it had no issues during installation. I then tried to ssh into the machine via PuTTy from another machine and as soon as I send the command, I get back a "connection refused" message.
I checked and port 22 is open (and it is using that port), and my router has that port open. Furthermore I am able to ssh into the machine if I use 127.0.0.1 and its local "192.168.x.x" addresses, however when I go to another source to check my IP and I use it, I get the error message. None of the posts or guides I looked at seemed to help.
I am using a Netgear router and I am using Verizon DSL. I've heard of people setting this up using that internet service, so I don't think they block the required port. I don't have a static IP, but I was going to set it up to notify me when the IP address changes so that isn't an issue.

Any help would be greatly appreciated.

---

### Post by Iowan on 2009-05-10
> **Glaciusor said:**
>  Furthermore I am able to ssh into the machine if I use 127.0.0.1 and its local "192.168.x.x" addresses, however when I go to another source to check my IP and I use it, I get the error message.Maybe I'm missing details... when you use the "192.168.x.x" address, is that from the machine itself? If so, have you tried connection from another machine connected either via crossover cable or hub/switch?

---

### Post by Glaciusor on 2009-05-10
Oh, sorry. It was between two machines linked (wirelessly) to a router, so a switch. That 192.168.x.x was grabbed from the ifconfig command.

---

### Post by Iowan on 2009-05-10
> **Glaciusor said:**
> Furthermore I am able to ssh into the machine if I use ... its local "192.168.x.x" addresses,Still fuzzy here (sorry... my confusion). You can successfully connect from the second machine via the router?  It's only from outside the local network (via Verizon DSL) that the connection fails?  
Once again, sorry for being dense...

---

### Post by Glaciusor on 2009-05-11
Yes, that's it. If I connect through the router it works fine, but if I try using the Internet I can't ssh into the server.

---

### Post by Iowan on 2009-05-11
The router is set up to forward port 22 to the 192.168.X.X address? (You might want to change that to a non-standard port to discourage the script kiddies.)

---

### Post by Glaciusor on 2009-05-13
I think that might have been the issue. I kinda messed up my modem though and I had to spend all my time at home fixing that. I thought I was in the router, but I changed some settings in the modem and that killed my internet connection, and I had to go through the whole verizon setup thing again... I am at college right now so I can't try but I think I know how to set that up. I was trying with a messed up internet connection earlier. Also, I'll heed your advice.

---

### Post by Glaciusor on 2009-05-16
Nope, I set up port forwarding on my router according to instructions I found online and I am still getting the connection refused error. This seems to be a problem with Netgear routers though, or so I've read. Does anybody know of any good (and reasonably priced) routers that I could use that actually work for port forwarding for ssh and ftp?

---

