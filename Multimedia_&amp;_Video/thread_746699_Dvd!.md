---
title: "Dvd!"
date: 2008-04-05
forum: Multimedia &amp; Video
---

### Post by Alex&amp;Linux on 2008-04-05
Ok boys and girls, I'm pretty ticked about this non-issue issue - my 64 bit 7.10 desktop will not play DVDs.

I have tried totem, VLC and I have downloaded every Gstreamer package and DVD library that is available.

Shouldnt there be a magic bullet solution to this problem?

By the way, its an HP Pavilion.

---

### Post by 1875 on 2008-04-05
libdvdcss installed ?

---

### Post by wolfen69 on 2008-04-05
in terminal:
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
then
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
then
```
sudo apt-get install libdvdcss2
```

---

### Post by Alex&amp;Linux on 2008-04-05
That worked, thanks!
Now, why is it necessary to download this?
Shouldnt it be included in the install CD?

---

### Post by wolfen69 on 2008-04-05
for legal reasons it cant be included on the cd. try linux mint (based on ubuntu) if you want every codec included.

---

