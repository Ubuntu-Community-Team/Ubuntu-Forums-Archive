---
title: "Cannot POP3 or IMAP into Gmail"
date: 2011-08-07
forum: Networking &amp; Wireless
---

### Post by blenderfox on 2011-08-07
Hi there,

I'm trying to connect to Gmail to pull my emails from the Gmail site, via the IMAP/POP3 access server. However, I can't seem to connect to the server when in Ubuntu:

```
momoko@yukinom:~$ telnet pop.gmail.com 110
Trying 209.85.143.109...


```

And it hangs here indefinitely. However, if I reboot my PC into Windows, it connects fine. I've turned off UFW so I would expect the connection to work. I've also been able to POP3 into other servers, so it seems to be something specific to the gmail IP.

Anyone else had the same problem or know how I can debug/fix this?

---

### Post by haqking on 2011-08-07
> **momokoyukino said:**
> Hi there,

I'm trying to connect to Gmail to pull my emails from the Gmail site, via the IMAP/POP3 access server. However, I can't seem to connect to the server when in Ubuntu:

```
momoko@yukinom:~$ telnet pop.gmail.com 110
Trying 209.85.143.109...


```And it hangs here indefinitely. However, if I reboot my PC into Windows, it connects fine. I've turned off UFW so I would expect the connection to work. I've also been able to POP3 into other servers, so it seems to be something specific to the gmail IP.

Anyone else had the same problem or know how I can debug/fix this?


try port 995

telnet pop.gmail.com 995

---

### Post by blenderfox on 2011-08-07
That worked! Thanks.

---

