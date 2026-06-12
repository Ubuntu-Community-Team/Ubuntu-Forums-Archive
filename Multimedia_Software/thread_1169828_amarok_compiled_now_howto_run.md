---
title: "amarok compiled now howto run?"
date: 2009-05-25
forum: Multimedia Software
---

### Post by henky on 2009-05-25
Hey guys, I just installed amarok

./configure
make
make install

now how do I run it, sorry for asking this but I'm kind of a noob!

Thnx!

p.s. I don't want to install via sudo apt-get install amarok

---

### Post by whoop on 2009-05-25
> **henky said:**
> Hey guys, I just installed amarok

./configure
make
make install

now how do I run it, sorry for asking this but I'm kind of a noob!

Thnx!

p.s. I don't want to install via sudo apt-get install amarok
Did you try:
```

./amarok

```
or
```

amarok

```

---

### Post by izizzle on 2009-05-25
```
amarok
``` should do it

---

### Post by henky on 2009-05-25
**./amarok **(in every directory I try gives me:)

bash: ./amarok: No such file or directory

and **amarok** gives me:
The program 'amarok' is currently not installed.  You can install it by typing:
sudo apt-get install amarok
bash: amarok: command not found


sudo apt-get install is not an option for me, since it'll install amarok 2

thnx anyway! any other way perhaps?

---

### Post by whoop on 2009-05-25
```

sudo find / -name amarok

```
To locate where the binary is...

---

