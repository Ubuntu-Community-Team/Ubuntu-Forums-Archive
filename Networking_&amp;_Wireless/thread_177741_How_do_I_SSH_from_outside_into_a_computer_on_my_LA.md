---
title: "How do I SSH from outside into a computer on my LAN"
date: 2006-05-16
forum: Networking &amp; Wireless
---

### Post by s|k on 2006-05-16
I can ssh into any of my computers within the lan from a computer in the lan, but how do I access my computers from outside the lan (i.e. from the internet via my IP). Before I had a LAN set up I could just ssh into my box using my home  systems IP, but now that I have several systems set up behind a router, I have no idea how to do this. I use a D-Link router, if that matters. 

Any help would be appreciated. Thanks!

---

### Post by nanotube on 2006-05-16
well, you would need to set up "port forwarding" in your router config, to forward port 22 to one of the computers on the inside of your lan. 
if you want to be able to ssh to multiple machines behind the lan, there are two solutions:
1. just ssh to the first one we have set up above, and then from that one ssh to any of the others
2. choose other ports, such as 23, 24, etc, and forward them each to a different machine's port 22, and then you can ssh directly to a bunch of machines, just by choosing the port number.

---

### Post by s|k on 2006-05-16
[QUOTE=nanotube]well, you would need to set up "port forwarding" in your router config, to forward port 22 to one of the computers on the inside of your lan. 
if you want to be able to ssh to multiple machines behind the lan, there are two solutions:
1. just ssh to the first one we have set up above, and then from that one ssh to any of the others
2. choose other ports, such as 23, 24, etc, and forward them each to a different machine's port 22, and then you can ssh directly to a bunch of machines, just by choosing the port number.[/QUOTE]
Thanks, that makes sense, yes I have port forwarding, I'll set that up.

---

### Post by nanotube on 2006-05-17
[QUOTE=s|k]Thanks, that makes sense, yes I have port forwarding, I'll set that up.[/QUOTE]
cool, have fun. just one word of warning: make sure to have strong passwords on your machines, so that they are not too easy to guess/bruteforce. once you have a service running and open to the world, best to be careful.

---

