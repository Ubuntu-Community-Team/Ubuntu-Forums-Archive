---
title: "Can Plustek OpticFilm 8100 scanner works on Ubuntu computer"
date: 2021-05-14
forum: Multimedia Software
---

### Post by satimis on 2021-05-14
Hi all,

Can Plustek OpticFilm 8100 scanner works on Ubuntu computer?

Regards

---

### Post by Holger_Gehrke on 2021-05-14
According to [sane-project.org]("http://sane-project.org/sane-mfgs.html#Z-PLUSTEK") it should be supported by the sane-genesys backend in the current version of libsane. You'll probably need to be on a very current Ubuntu; 21.04 ships with 1.0.32 which is the current version AFAIK; 20.04 has 1.0.29 and that seems to be missing support for that device. The Genesys backend seems to have gone through a growth spurt recently, I remember a time not too long ago when scanners using those chips - like the HP I used to own back when I was still dual booting - were basically unusable in Linux.

Holger

---

### Post by satimis on 2021-05-14
Hi Holger,

Thanks for your advice.

Regards

---

### Post by Flash858 on 2021-05-20
There is a project:

[https://plustek.com/us/software/linuxaction/index.php](https://plustek.com/us/software/linuxaction/index.php)

---

