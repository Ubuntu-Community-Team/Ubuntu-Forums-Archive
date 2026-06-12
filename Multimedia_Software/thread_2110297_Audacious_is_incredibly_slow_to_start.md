---
title: "Audacious is incredibly slow to start"
date: 2013-01-29
forum: Multimedia Software
---

### Post by mc-rpg on 2013-01-29
Audacious is incredibly slow to start (a full 20 seconds) after I try to play songs with it be it from the "open with" menu from nautilus or simply starting it through the dash. I don't know why this is, does somebody else experience this? My machine is decent (dell inspiron 14z N411z), and my ubuntu version 12.10

Thanks in advance.

---

### Post by cybrsaylr on 2013-01-29
Audacious starts, loads fast and is acting totally normal for me with 12.04. I like and use Audacious a lot. No problems here.

---

### Post by mc-rpg on 2013-01-29
I know my situation must be unusual. I'm thinking maybe 64bits has something to do with it?

---

### Post by tgalati4 on 2013-01-29
Try running audacious in a terminal.  Post anything interesting.  In another terminal:

```
dmesg | tail -50
```

---

### Post by mc-rpg on 2013-01-29
Apparently I was using an updated (3.3.3 version) version from webupd8 repository, I downgraded to the regular multiverse one and it isn't slow to start anymore. Thanks for the help.

---

### Post by cybrsaylr on 2013-01-29
> **mc-rpg said:**
> I know my situation must be unusual. I'm thinking maybe 64bits has something to do with it?

I've been using 64 bit versions for years with no issues.

---

### Post by mc-rpg on 2013-01-29
Ok, it wasn't the updated version that was giving me problems, it was actually the scrobbler plugin. It was kind of buggy and the old version started to behave the same way after enabling it. I disabled it now and don't experience the problem, on the older or updated version. 

Thanks again.

---

