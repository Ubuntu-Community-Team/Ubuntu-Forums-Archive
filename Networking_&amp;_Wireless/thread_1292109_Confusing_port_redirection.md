---
title: "Confusing port redirection"
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by effigies on 2009-10-15
I am running a Tomcat server on port 8080, and need it accessible to port 80.

Now, I don't really want to run this as root, nor do I want to install Apache and just give a HTTP redirect to :8080.

So, I've looked to the internet, and found variations on this advice:

```
iptables -t nat -A PREROUTING -i eth0 -p tcp -dport 80 -j REDIRECT --to-port 8080
```

And this works... sort of.

Much of the time it works fine, but it will sometimes hang, or take a long time to load (after the first such page, it usually works fine). I've found that if I point my browser to host:8080, and then go back to host:80, it will work fine as well. So it seems to be getting caught handling new connections at times.

Anyway, this really isn't acceptable behavior, so I looked around, and I found the rinetd package. And it has the *exact* same behavior. Fine once you visit :8080, sometimes hanging or taking forever if you don't.

I hope somebody else out there is having this issue, because it's driving me mad.

---

### Post by yknivag on 2009-10-15
Wouldn't it be easier just to set Tomcat to listen on port 80?

---

### Post by effigies on 2009-10-19
Supposing I wanted to run it as root, yes.

---

### Post by yknivag on 2009-10-20
Why would you need to run it as root? Is there no config option in Tomcat to allow you to change the port it listens on?

---

### Post by effigies on 2009-10-27
Ports 1-1024 are reserved for the system, and can only be opened by root.

---

