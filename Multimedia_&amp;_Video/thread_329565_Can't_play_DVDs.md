---
title: "Can't play DVDs"
date: 2007-01-01
forum: Multimedia &amp; Video
---

### Post by TheMatt on 2007-01-01
:-k For some reason, Kubuntu can't read any DVDs. Everytime I put one in, the program will either not be able to navigate the menus, or it will just crash right before the menu appears with no error message. I have tried KMPlayer, Kaffiene, Totem, GXine, and Ogle, and all have the same result. What can I do? Thanks in advance.

---

### Post by meng on 2007-01-01
Have you installed libdvdread?

---

### Post by obsidion on 2007-01-01
> **TheMatt said:**
> :-k For some reason, Kubuntu can't read any DVDs. Everytime I put one in, the program will either not be able to navigate the menus, or it will just crash right before the menu appears with no error message. I have tried KMPlayer, Kaffiene, Totem, GXine, and Ogle, and all have the same result. What can I do? Thanks in advance.

  Try firing up one or more of them from a konsole and seeing what the errors are.
I take it you have visted 

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

and made sure you have all the relevant bits installed ?

---

### Post by TheMatt on 2007-01-01
Thanks. I have installed libdvdread3 as well as libdvdcss2. I will take a thorough look at the page tomorrow when I have a chance.

---

### Post by TheMatt on 2007-01-02
I found the answer. Installing this and installing the AUD-DVD and Multimedia codecs worked.
[http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29)

---

