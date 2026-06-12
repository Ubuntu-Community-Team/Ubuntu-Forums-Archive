---
title: "What Does This Mean?"
date: 2008-04-25
forum: Multimedia Software
---

### Post by Mark76 on 2008-04-25
I get this same message every time I run cdrdao scanbus

> Error trying to open /dev/sg5 exclusively (Permission denied)

What does it mean and how can I stop it?

---

### Post by andrew.46 on 2008-04-26
Hi,

Try running the command with sudo:

```
$ sudo cdrdao scanbus
```

    Andrew

---

### Post by Mark76 on 2008-04-26
Damn.

cdrdao doesn't support my driver :(

---

### Post by andrew.46 on 2008-05-19
Hi:

> **Mark76 said:**
> cdrdao doesn't support my driver :(

I suspect that it probably does. Just use the default driver in your commandline: --driver generic-mmc

     Andrew

---

