---
title: "Nautilus sorting changed?"
date: 2010-05-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2010-05-28
Upper case letters seem to get a higher lexicgraphical priority than lower case letters:

Example folders:```
A
BZ
Ba
Z
a
b
z
```

WTF!?

---

### Post by wayneericgouin on 2010-05-28
If by that you mean the order Nautilus sorts files and folders then I haven't noticed. I created a folder with the name aardvark in my home directory and it was sorted first in line.

---

### Post by philinux on 2010-05-28
Seems the default is lowercase folders then uppercase followed by lower case files then upper.

---

### Post by wayneericgouin on 2010-05-28
I see, I guess I just didn't even notice that, I am seeing it now though.

---

### Post by MacUntu on 2010-05-28
Maybe my system is borked, will try another one.

Here's how it looks for me:

[IMG]http://img.xrmb2.net/images/817668.png[/IMG]

**Edit:**

Well, everything's right with my second Meerkat, so it's a false alarm. Now I just have to figure out why it's wrong on this machine.

---

### Post by wayneericgouin on 2010-05-28
here's mine

---

### Post by MacUntu on 2010-05-28
Guess I've found the problem:
```
$ locale
LANG=C
LC_CTYPE="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_COLLATE="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_PAPER="C"
LC_NAME="C"
LC_ADDRESS="C"
LC_TELEPHONE="C"
LC_MEASUREMENT="C"
LC_IDENTIFICATION="C"
LC_ALL=
```

No idea who did this.

---

### Post by zika on 2010-05-28
```
$ locale
LANG=en_US.utf8
LC_CTYPE="en_US.utf8"
LC_NUMERIC="en_US.utf8"
LC_TIME="en_US.utf8"
LC_COLLATE="en_US.utf8"
LC_MONETARY="en_US.utf8"
LC_MESSAGES="en_US.utf8"
LC_PAPER="en_US.utf8"
LC_NAME="en_US.utf8"
LC_ADDRESS="en_US.utf8"
LC_TELEPHONE="en_US.utf8"
LC_MEASUREMENT="en_US.utf8"
LC_IDENTIFICATION="en_US.utf8"
LC_ALL=
```

---

### Post by MacUntu on 2010-05-28
How do I set this back to "en_US.UTF-8"? It's definitely the problem:```
$ printf 'A\na\nBZ\nBa' | LC_COLLATE=C sort
A
BZ
Ba
a
$ printf 'A\na\nBZ\nBa' | LC_COLLATE=en_US.UTF-8 sort
a
A
Ba
BZ
```

---

### Post by MacUntu on 2010-05-28
Sorry for spamming. See [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/506396](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/506396)

Turned out the value for 'Language' in ~/.dmrc was set to 'C' instead of en_US.UTF-8. 

Everything's fine now. :)

---

