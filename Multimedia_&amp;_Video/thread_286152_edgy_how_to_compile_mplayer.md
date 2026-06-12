---
title: "edgy how to compile mplayer?"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by ghosthead123 on 2006-10-27
I download the last mplayer + codecs and try to compile it with:
./configure --enable-gui 

but after a few seconds shows up this:
Checking for GTK+ version ... GTK-2 devel packages were not found, trying GTK 1.2
Checking for GTK version ... 
Error: The GUI requires GTK devel packages (which were not found).

---

### Post by raul_ on 2006-10-27
go to synaptic and install the gtk-dev packages. Probably version 2

---

### Post by Conq on 2006-10-27
You can use apt to get all the dependencies you need automatically:

```

sudo apt-get build-dep mplayer

```

Will get you all the dependencies the ubuntu team has used to build their version of the package. Of course you need the appropriate deb-src lines in your sources.list for this to work. Happy hacking!

---

