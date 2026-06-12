---
title: "How to Install Quod Libet 1.0"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by themeone on 2007-10-20
Can anyone tell me how to install Quod Libet 1.0 from the tarball?

I have downloaded and unpacked both mutagen and quodlibet tarballs.  I have installed mutagen according to the README file, but the README file for in the quodlibet directory contains no installation instructions, nor do they appear to be anywhere else.

---

### Post by hugmenot on 2007-10-20
If you have Ubuntu 7.10 you can install it simply from the package repository.

If not andif you want it quickly, you can use the [packages for Feisty]("http://ubuntuforums.org/showpost.php?p=2596985&postcount=201") that I made recently.

If you want to install from source you have to use the setup.py script.

```
./setup.py build
sudo ./setup.py install
```

Both for Mutagen and QL, and you have to install all the build dependencies first.

---

### Post by themeone on 2007-10-21
Now you've reminded me, that's how I remember doing it on previous installs.

However, on this occasion although what you said works for Mutagen, it didn't work for QL.  There was no setup.py in the extracted directory and I had to do

```
./quodlibet.py build
sudo ./quodlibet.py install
```

Maybe they changed it.

---

