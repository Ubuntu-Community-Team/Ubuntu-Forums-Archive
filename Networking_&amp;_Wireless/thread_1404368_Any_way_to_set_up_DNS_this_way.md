---
title: "Any way to set up DNS this way?"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by Hawk__0 on 2010-02-11
I run Ubuntu in a domain with windows DNS.  I'm wondering if I can change ubuntu's configuration so that I dont have to do this:

```
ping computer.domain.com
```

I want to be able to do this:

```
ping computer
```

Is this possible?  /etc/hosts modification perhaps?

---

### Post by pirateghost on 2010-02-11
> **Hawk__0 said:**
> I run Ubuntu in a domain with windows DNS.  I'm wondering if I can change ubuntu's configuration so that I dont have to do this:

```
ping computer.domain.com
```I want to be able to do this:

```
ping computer
```Is this possible?  /etc/hosts modification perhaps?


what is in your /etc/resolv.conf file?

---

### Post by i.r.id10t on 2010-02-11
add the line

search yourdomain.com

to /etc/resolv.conf

---

### Post by Hawk__0 on 2010-02-11
> **i.r.id10t said:**
> add the line

search yourdomain.com

to /etc/resolv.conf

Thought I had that already :P, thanks!

---

### Post by Iowan on 2010-02-11
Just my (unsolicited) opinion - that sounds like  DNS (server) configuration.

---

