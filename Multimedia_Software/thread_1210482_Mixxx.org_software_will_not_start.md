---
title: "Mixxx.org software will not start"
date: 2009-07-11
forum: Multimedia Software
---

### Post by andrewlewis1114 on 2009-07-11
I just installed Mixxx 1.6.1 on ubuntu 9.04, and it will not open. It installs just fine but then once i try to run it, nothing happens. Anyone else have this problem?

---

### Post by raboofje on 2009-07-11
> **andrewlewis1114 said:**
> I just installed Mixxx 1.6.1 on ubuntu 9.04, and it will not open. It installs just fine but then once i try to run it, nothing happens. Anyone else have this problem?

Does it print any enlightening messages when started from the command-line?

---

### Post by Crafty Kisses on 2009-07-11
> **andrewlewis1114 said:**
> I just installed Mixxx 1.6.1 on ubuntu 9.04, and it will not open. It installs just fine but then once i try to run it, nothing happens. Anyone else have this problem?

I had the exact same problem with Mixxx. I solved this issue by opening a Terminal and running:
```
sudo mixxx
```

---

### Post by raboofje on 2009-07-14
> **Codename said:**
> I had the exact same problem with Mixxx. I solved this issue by opening a Terminal and running:
```
sudo mixxx
```

There really should be a way to run this application without resorting to running it as root. This might cause trouble, for example when using it with JACK, or crash your machine if it runs afoul.

---

