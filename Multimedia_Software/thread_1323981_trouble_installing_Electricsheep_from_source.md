---
title: "trouble installing Electricsheep from source"
date: 2009-11-12
forum: Multimedia Software
---

### Post by TechnoJunky on 2009-11-12
I'm trying to install ElectricSheep screensaver from source.  I had some other dependancy problems, but figured them out, but I can't get this one.  Configure runs smoothly but make fails here:

gcc -DPACKAGE_DATA_DIR=\"/usr/local/share/electricsheep\" -g -O2   -o electricsheep electricsheep.o getdate.o utils.o md5.o -lavformat -lavcodec -lavutil -lm -lz -lexpat
/usr/bin/ld: cannot find -lavformat
collect2: ld returned 1 exit status
make[1]: *** [electricsheep] Error 1
make[1]: Leaving directory `/home/carl/Downloads/electricsheep-2009-11-04/client'
make: *** [all] Error 2

---

### Post by andrew.46 on 2009-11-12
Hi TechnoJunky,

> **TechnoJunky said:**
> ```
/usr/bin/ld: cannot find -lavformat
```

The [installation script]("http://electricsheep.org/makesheep.sh") from the Electricsheep site suggests *libavformat-dev* as well as a few others.

All the best,

Andrew

---

### Post by TechnoJunky on 2009-11-13
That script worked beautifully.  I had the source code from a previous installation, and when I upgraded to 9.10, tried the same source code but didn't download the script.  Thank you!

---

### Post by andrew.46 on 2009-11-13
Hi TechnoJunky,

> **TechnoJunky said:**
> That script worked beautifully.  I had the source code from a previous installation, and when I upgraded to 9.10, tried the same source code but didn't download the script.  Thank you!

Excellent news :). Now having had a quick look at the whole Electricsheep thing I might install it myself, it looks quite interesting!

Andrew

---

