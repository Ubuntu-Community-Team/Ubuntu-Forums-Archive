---
title: "Postfix attempting to send on port 26. How to change it to send on 25?"
date: 2011-11-02
forum: Networking &amp; Wireless
---

### Post by Achetar on 2011-11-02
I'm attempting to fix a broken mail system on an Ubuntu Server so that our PHP mail() function will work. (because thats all we use this for). I've been trying to fix it for almost two weeks now and cannot figure out what the cause of the problem is.

Every mail that attempts to get sent times out. Every mail is also attempting to be sent to port 26. I've already purged and re-installed postfix in an attempt to fix this, but it did not succeed. A sample of  the error:

```

Nov  2 08:38:22 truwow postfix/smtp[28979]: connect to alt3.gmail-smtp-in.l.google.com[209.85.227.26]:26: Connection timed out

```

It doesn't matter which service I try to send to (gmail, hotmail, etc), they all time out. In addition, they all try to go to port 26. I can telnet in to port 25 of all of the services from the server, so the port is not blocked.

What's causing it to attempt to send on port 26 and how can I change it so that its sending on port 25?

---

### Post by Achetar on 2011-11-02
Bump and, uh, oops. I meant to post this in Networking support instead of Security. Could a moderator move it?

---

### Post by cariboo on 2011-11-03
A bump for the move.

---

