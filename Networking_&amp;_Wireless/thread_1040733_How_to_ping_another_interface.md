---
title: "How to ping another interface?"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by Thradya on 2009-01-15
Configuration:

eth0 - 192.168.1.1
eth1 - 10.0.0.1

and a router between them.

I need to make external loop and send traffic from one interface to another through the router.
Is that possible? If yes, how?

Simple "route add 192.168.1.1 dev eth1" doesn't work.
Any ideas?

Thank you.

---

### Post by superprash2003 on 2009-01-16
you would need to use iptables for this.. its similar to this [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370) .. where data is forwarded from one interface to another

---

### Post by Thradya on 2009-01-18
Thank you.
However I managed to accomplish it with VirtualBox.

---

### Post by lensman3 on 2009-01-18
You also have to do:

echo "1" > /proc/sys/net/ipv4/ip_forward

You have to turn on forwarding.

---

### Post by Thradya on 2009-01-18
> **lensman3 said:**
> You also have to do:

echo "1" > /proc/sys/net/ipv4/ip_forward

You have to turn on forwarding.

OK, I didn't get it.
Isn't ip_forward used for forwarding packets from one subnetwork to another INTERNALLY?
Like when computer from one subnetwork wants to ping computer from another subnetwork, then we set ip_forward on the router to 1?
Dunno what it has to do with my problem.

---

