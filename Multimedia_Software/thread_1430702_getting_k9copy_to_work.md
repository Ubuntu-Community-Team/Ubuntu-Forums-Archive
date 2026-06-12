---
title: "getting k9copy to work"
date: 2010-03-15
forum: Multimedia Software
---

### Post by geovino on 2010-03-15
I just installed 9.10 64bit on a new hard drive and ran the restricted drivers package which run most audio visual programs, but I can't get k9copy to work. I did a apt-get install libdvdcss2 w32codecs, but neither would install. 

What am I missing that will run k9copy and other multi-media programs?

---

### Post by mc4man on 2010-03-15
w32codecs don't go on a 64bit install, there is w64codecs but they're pretty much worthless

Anyway k9 doesn't use either, to get libdvdcss2 run this or [go here and grab]("http://packages.medibuntu.org/karmic/libdvdcss2.html")
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

I believe the newer k9 has 2 menu entries - you may find the 'k9copy assistant' useful if you've never used k9 before

---

### Post by geovino on 2010-03-15
Thanks a lot. It's working now. :)

---

### Post by chuckycheese on 2010-03-17
ran k9copy and got a file that is 13.2 Gb, from a 7.5 Gb disk, what went wrong? K3 can't burn a file this big!

---

