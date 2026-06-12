---
title: "CUPS blocks me from logging into admin page"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by jvofvnopz on 2010-11-16
Hello,
I am attempting to connect my new Brother HL-2230 printer over CUPS. However, when I try to log in to [http://localhost:631/admin](http://localhost:631/admin) it asks me for authentication. When I enter the user name for my administrator account (limao) and password, it reprompts me for my username and password again. using
```

# lppasswd -a limao
Enter password:
Enter password again:

```
was no help at all. I even added 
```

  AuthType Default
  Require user @OWNER @SYSTEM

```
inside the <Location /admin></Location> tags.
And yes, I did restart CUPS in between each iteration.
Can someone please explain my mistake?

P.S. I have the "guarddog" firewall installed and active, but I did add an ALLOW exception for port 631.

---

### Post by jvofvnopz on 2010-11-16
Oh haha... a quick system reboot fixed my issues ;)

---

