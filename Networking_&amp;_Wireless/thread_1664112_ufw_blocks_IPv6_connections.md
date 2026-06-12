---
title: "ufw blocks IPv6 connections"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by ygoe on 2011-01-10
Hi,

I've just started using ufw with the frontend gufw. I've configured it like this:

Accept everything in and out as default
Block incoming FTP connections from a certain IPv4 address (brute-force for days)

Today I noticed that IPv6 connections don't work anymore. The connection to two hosts (IPv6 only) times out. As soon as I disable ufw entirely, the connections work again. The host I want to connect to is:
2001:638:a00:f00b:200:1cff:fedb:d38f port 7337
2001:638:a00:f00b:a00:6ff:fe07:cda2 port 7337
These are small telnet servers that print out a number (temperature nearby) and close again. I'm logging those values in a database.

Is ufw not IPv6-capable and blocks things it's not supposed to?

Update: ufw seems complete garbage to me... You can't even configure it while it's disabled! How am I supposed to safely activate it when the first thing it does is blocking all communications? I can't even configure it to let me in before I configure it to keep me out... And then, even if I explicitly let it pass port 7337, it still blocks it through IPv6. While the idea is certainly nice, I don't think this could be useful to me. I guess I need to write my own rufw (really uncomplicated - and working).

---

### Post by PatchesTheCaveman on 2011-01-11
Edit your */etc/default/ufw* file and change the line that says:
```
IPV6=no
```
to
```
IPV6=yes
```

---

### Post by ygoe on 2011-01-11
Thanks, that seems to help. I wonder what this firewall also blocks if not configured otherwise in some config files documented in a hidden spot... Time will tell.

---

### Post by marquinos on 2011-01-12
> **LonelyPixel said:**
> You can't even configure it while it's disabled!
Uhm, you can have ufw disabled, add rules and enable. All will works.

---

### Post by ygoe on 2011-01-12
Then is gufw really such a stupid hack that it doesn't allow that?

---

