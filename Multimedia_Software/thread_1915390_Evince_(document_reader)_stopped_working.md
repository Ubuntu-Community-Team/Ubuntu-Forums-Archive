---
title: "Evince (document reader) stopped working"
date: 2012-01-26
forum: Multimedia Software
---

### Post by lads on 2012-01-26
Hello everyone,

Evince has stopped working today, when I click on a pdf file nothing happens, no error messages, no warnings, nothing. The same thing if I try to start Evince from the menu.

How can I debug this? Or send some more information?

Any alternatives to Evince worth noting?

Thank you.

---

### Post by MoreOrLess on 2012-01-26
Start evince from the terminal..

---

### Post by lads on 2012-01-26
> **MoreOrLess said:**
> Start evince from the terminal..

Nothing:

```
$ cd /usr/lib/evince
$ ./evinced
$
```

Any way to get debug messages?

Thanks

---

### Post by lads on 2012-01-27
Evince is working fine again today, go figure. I suspect the kernel update 2 days might have broken something that was fixed with the updates this morning. I'll flag this issue as solved for now.

---

