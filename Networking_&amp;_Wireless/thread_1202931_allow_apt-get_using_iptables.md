---
title: "allow apt-get using iptables"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by doobie on 2009-07-02
What is the minimal (or most secure) way of allowing apt-get to work using iptables?  Right now, I have dns working but am having trouble getting the connection (port 80, 21 ?) working.

---

### Post by computer13137 on 2009-07-02
I don't know about anyone else, but I'm confused as to what you're trying to do.

apt-get is an outgoing connection request, I don't see why iptables would be blocking it.

Are you like, trying to run your own repository or something?  As far as I know, apt-get only uses port 80 regular old HTTP.  If you can browse the web on the machine, I don't see why apt-get wouldn't work too.

-Kirk

---

### Post by doobie on 2009-07-02
I deny all outgoing by default and would like to allow only the outgoing connections that are required to connect to apt-get repositories and download updates (i.e., so "sudo apt-get update" and "sudo apt-get upgrade outdated" work).

---

### Post by alphacrucis2 on 2009-07-02
> **doobie said:**
> I deny all outgoing by default and would like to allow only the outgoing connections that are required to connect to apt-get repositories and download updates (i.e., so "sudo apt-get update" and "sudo apt-get upgrade outdated" work).

As far as I know apt-get only uses tcp port 80 to connect to the repo servers.

---

### Post by superprash2003 on 2009-07-03
you could use gufw to get better control over allowing/denying traffic/ports

---

