---
title: "Opening Ports"
date: 2006-05-05
forum: Networking &amp; Wireless
---

### Post by z3snap on 2006-05-05
Is there anyway I can open ports without the use of firestarter(isn't working correctly) or any other GUI firewall?

---

### Post by neouser99 on 2006-05-05
all the ports are already open unless you specifically installed a firewall. that is on the box, that doesn't mean that if you have a nat-ed network that the firewall in front of your machine isn't forwarding the ports, or  you isp isn't blocking the port.

-neo

---

### Post by z3snap on 2006-05-05
will I just installed Breezy Badger and noticed all the ports r closed...also I'm connect though my schools ethrenet.

---

### Post by nanotube on 2006-05-05
check out the first link on my sig, and go to the firewall section.
that will show you how to configure iptables directly.

but like the previous poster said, if you are also behind a nat/router, you need to have it forward the right ports.

---

### Post by neouser99 on 2006-05-05
what is telling you all the ports are closed?? are you running nmap or something like this? and from where are you scanning (relative to your location)?

-neo

---

### Post by z3snap on 2006-05-05
yes I ran nmap and also used that netstat scan, but I will try that link from nanotube thanx.

---

### Post by neouser99 on 2006-05-05
netstat won't show up which ports are open, and depeding on where the nmap is coming from, its probably telling you that nothing on the university firewall is open.

-neo

---

