---
title: "disk check ?"
date: 2010-07-15
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ronacc on 2010-07-15
whats the command to check a hard disk ? I'm having a senior moment and can't find it .

---

### Post by taavikko on 2010-07-15
For ext filesystem
e2fsck

---

### Post by ronacc on 2010-07-15
thank you

---

### Post by dino99 on 2010-07-15
fsck -n /dev/sdxx to "check"

fsck -y /dev/sdxx to repair

*** sdxx = your partition

showfsck let you know what the history is

---

