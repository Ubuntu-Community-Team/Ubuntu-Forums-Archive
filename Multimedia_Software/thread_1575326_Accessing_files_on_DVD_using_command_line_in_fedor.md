---
title: "Accessing files on DVD using command line in fedora"
date: 2010-09-15
forum: Multimedia Software
---

### Post by bbuy2k on 2010-09-15
Hey family,

I'm trying to access the contents on a fedora install DVD using the command line, but I'm having some trouble. I can access my thumb drives with no problem because its all one word, but the dvd is multiple words (ex. Fedora 13 i386 DVD). I am trying to copy a file from the dvd into a folder I created. How do I go about doing that?

Please help,

bbuy2k

---

### Post by bbuy2k on 2010-09-15
Hey family,

I'm trying to access the contents on a fedora install DVD using the command line, but I'm having some trouble. I can access my thumb drives with no problem because its all one word, but the dvd is multiple words (ex. Fedora 13 i386 DVD). I am trying to copy a file from the dvd into a folder I created. How do I go about doing that?

Please help,

bbuy2k

---

### Post by andrew.46 on 2010-09-16
Hi bbuy,

You can simply enclose the file path as follows:

```
cp **[COLOR="Red"]'[/COLOR]**my path/Fedora 13 i386 DVD/my file**[COLOR="Red"]'[/COLOR]** destination
```

and of course alter the path and filename to suit your actual needs :).

Andrew

---

### Post by bbuy2k on 2010-09-16
Thanks Andrew I'll try it and report back A.S.A.P.

---

