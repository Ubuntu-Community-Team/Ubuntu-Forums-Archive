---
title: "Installing lives video editing software"
date: 2009-10-21
forum: Multimedia Software
---

### Post by jabberwok on 2009-10-21
I managed to install all the dependencies listed in the readme including the recommended ones.Only thing I could not find was

gdk-pixbuf-loaders

I did ./configure  ..ok   make...  ok


sudo make install gives this error


MP -MF .deps/main.Tpo -c -o main.o main.c
main.c: In function ‘lives_init’:
main.c:1490: error: invalid storage class for function ‘lives_startup’
main.c: In function ‘lives_startup’:
main.c:1520: warning: passing argument 1 of ‘lives_init’ from incompatible pointer type
main.c: In function ‘lives_init’:
main.c:1685: warning: ‘main’ is normally a non-static function
main.c: In function ‘main’:
main.c:1688: error: request for member ‘ign_clipset’ in something not a structure or union
main.c:1688: error: request for member ‘ign_osc’ in something not a structure or union
main.c:1688: error: request for member ‘ign_jackopts’ in something not a structure or union
main.c:1688: error: request for member ‘ign_aplayer’ in something not a structure or union
main.c:1780: error: request for member ‘ign_clipset’ in something not a structure or union
main.c:1787: error: request for member ‘ign_clipset’ in something not a structure or union
main.c:1821: error: request for member ‘ign_aplayer’ in something not a structure or union
main.c:1835: error: request for member ‘ign_osc’ in something not a structure or union
main.c:1841: error: request for member ‘ign_osc’ in something not a structure or union
main.c: In function ‘lives_init’:
main.c:2572: error: invalid storage class for function ‘get_max_opsize’
main.c:4169: error: expected declaration or statement at end of input
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/neill/Desktop/lives/src'
make: *** [all-recursive] Error 1

Any ideas

I am desperately trying to get software that can remove the blue screen from a video (linear color?) to produce transparent background on flash

Also failed to install jahshaka

---

### Post by mc4man on 2009-10-21
For jaunty or earlier it probably was this

libgdk-pixbuf-dev

Anyway maybe just use a pre-built from here (1.1.4

[http://www.getdeb.net/release/4941](http://www.getdeb.net/release/4941)

edit: karmic has the 1.1.2 ver. in repo

---

### Post by jabberwok on 2009-10-21
installing libgdk-pixbuf-dev failed to solve the problem

I have installed the trial version of adobe after effects

so I will wait for Karmic

---

