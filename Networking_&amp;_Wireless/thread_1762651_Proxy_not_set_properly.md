---
title: "Proxy not set properly"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by sreeve29 on 2011-05-19
When I installed Ubuntu 11 Server, it asked for a proxy http address.  I gave it our address, I'll call it a.b.c.d.

It did not, however, prompt for the port number (8080).

Now, when I do the following:

sreeve@pto:~$ !20
sudo apt-get update
0% [Connecting to a.b.c.d (a.b.c.d)] [Connecting to a.b.c.d (a.b.c.d)]

it just sits there for a while and then says:

unable to connect to a.b.c.d

Is there a way to give it a proxy http address with the port number also?

---

### Post by sreeve29 on 2011-05-19
Problem solved.  Just had to add the ":8080" into /etc/apt/apt.conf:

Acquire::http::Proxy "http://16.213.0.40:8080";

---

