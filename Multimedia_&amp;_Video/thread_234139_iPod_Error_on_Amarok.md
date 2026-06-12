---
title: "iPod Error on Amarok"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by Sentinel on 2006-08-11
apparently when i add device i get this message

Media Device: failed to create lockfile on iPod mounted at /media/ipod: Read-only file system

i did remove and add over and over, and i still get the same message, anything im doing wrong here?

---

### Post by jordilin on 2006-08-11
> **Sentinel said:**
> apparently when i add device i get this message

Media Device: failed to create lockfile on iPod mounted at /media/ipod: Read-only file system

i did remove and add over and over, and i still get the same message, anything im doing wrong here?

Try:
```
chmod +w /media/ipod
```
to have write permissions

---

### Post by Sentinel on 2006-08-11
exatly where do i type that code

---

### Post by jordilin on 2006-08-11
> **Sentinel said:**
> exatly where do i type that code
Open a Terminal (applications->Accessories) and then type 
```
chmod +w /media/ipod
```
Is that what you mean?

---

### Post by Sentinel on 2006-08-12
still dealing with the same problem

---

### Post by datakid on 2007-01-30
> **jordilin said:**
> Try:
```
chmod +w /media/ipod
```
to have write permissions

I did this and my error changed to "Media Device: No mounted iPod found", which is also not true?

---

