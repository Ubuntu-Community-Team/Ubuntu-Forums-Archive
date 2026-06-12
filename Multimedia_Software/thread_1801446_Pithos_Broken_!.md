---
title: "Pithos Broken !?"
date: 2011-07-10
forum: Multimedia Software
---

### Post by Derek Karpinski on 2011-07-10
Pithos is my most widely used application in Ubuntu.  I simply love it.  It worked great last night, but now, I get this error:

```
Error

Pandora does not support your client version.
```

Is pandora pushing out some changes that break pithos?

---

### Post by Derek Karpinski on 2011-07-10
Solved by adding the ppa for the daily build:

```
ppa:kevin-mehall/pithos-daily
```

---

### Post by markyblue on 2011-07-14
For the inexperienced user out there (me) how do you add that ppa? I don't even know what a "ppa" is. Pithos has been a great find for me, and I would love to have it working again. 

If you have any more help on this I would appreciate it. Thanks

---

### Post by markyblue on 2011-07-14
I tried to add this code into the terminal, but I still get the same error message

sudo add-apt-repository ppa: kevin-mehall/pithos-daily

---

### Post by markyblue on 2011-07-14
I just removed the application, then added it again through the Software Center, I'm back up and running again.:D

---

### Post by buckmaster60 on 2011-07-16
none of this worked until i aptitude update then upgrade.  python needed to be upgraded as pithos uses python

---

### Post by Indo_Network on 2011-07-16
> **Derek Karpinski said:**
> Pithos is my most widely used application in Ubuntu.  I simply love it.  It worked great last night, but now, I get this error:

```
Error

Pandora does not support your client version.
```Is pandora pushing out some changes that break pithos?
..........................

---

