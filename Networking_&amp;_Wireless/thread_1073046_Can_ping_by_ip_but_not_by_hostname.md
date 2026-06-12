---
title: "Can ping by ip but not by hostname"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by spegru on 2009-01-29
I'm having a related problem with Intrepid
I can ping my PC via its IP address but it doesn't recognise the hostname



Any ideas?

spegru

---

### Post by albinootje on 2009-01-29
> **spegru said:**
> I'm having a related problem with Intrepid
I can ping my PC via its IP address but it doesn't recognise the hostname


Did you edit /etc/hosts for filling in the ip addresses of your machine(s) ?

---

### Post by spegru on 2009-01-29
No I didn't. Why should I have to do that? - it's supposed to be automatic with DNS and it has worked that way before in both windows and linux too.
Is it a bug?

---

### Post by albinootje on 2009-01-29
> **spegru said:**
> No I didn't. Why should I have to do that? - it's supposed to be automatic with DNS and it has worked that way before in both windows and linux too.
Is it a bug?

You should provide some more details about your setup, before, and now.

---

### Post by spegru on 2009-02-17
Previously Hardy, now Intrepid.
Normal DSL router home network that provides (or provided) DNS and DHCP

Anything else?

I now see that at static address is usually recommended for print serving. But I still don't understand why I can't simply give a host name

---

### Post by albandy on 2009-02-17
Have you added the auto eth0 sentence in /etc/network/interfaces ?

---

### Post by dmizer on 2009-02-17
Split this off into it's own thread because it wasn't related.

Thank you, carry on.

---

