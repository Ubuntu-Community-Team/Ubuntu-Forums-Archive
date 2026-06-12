---
title: "Unable to use Asunder to rip a CD"
date: 2012-12-07
forum: Multimedia Software
---

### Post by adamaphar on 2012-12-07
I recently bought a laptop with Ubuntu installed (12.10)

I would like to rip CDs. I downloaded Asunder. When I  insert a CD nothing at all happens. Asunder makes no indication that it is aware of a CD there. The "Rip" button is grayed.

Any ideas?

Thank you in advance

---

### Post by Jason80513 on 2012-12-07
Have you tried Thoggen? It's relatively simple to use, and if it doesn't work it usually indicates you need to install ubuntu-restricted-extras or some such packages. Works for most DVDs, but not some of the Disney DVDs.

(All DVDs I rip, I own.)

---

### Post by cottfcfan on 2012-12-08
Make sure that under preferences/general the path to your CDROM is correct. In mine it is /dev/cdrom. But it may vary on different hardware.
As mentioned above it's also a good idea to install ubuntu-restricted-extras.
```
sudo apt-get install ubuntu-restricted-extras
```

---

