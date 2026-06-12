---
title: "jaaa"
date: 2006-08-13
forum: Multimedia &amp; Video
---

### Post by edev on 2006-08-13
Hello sound men,

Has anybody successfully installed jaaa on his Dapper box ?

I installed it using rpms from planet CCRMA, resolved de depndencies but now I'm facing an error telling me that he cannot find libjack.so.0. Must be a symlink or something like that ?

Jack is installed working A1.

I don't want to mess-up with jack version since I'm trying to install jaaa on my main studio machine.

Thanx a lot for helping,

Eric,

---

### Post by edev on 2006-08-13
Ok, here's something a little cleaner... Sorry about the previous post.

I compiled the deps (clalsadrv-1.1.0-1.tar.bz2 - clthreads-2.2.0-1.tar.bz2
clxclient-3.3.0-1.tar.bz2) worked fine. When I tried to compile either aeolus or jaaa, exit with this error :

=====================

make
g++  -O3 -Wall -MMD -MP -DVERSION=\"0.6.6\" -DLIBDIR=\"/usr/lib\"  -c -o main.o main.cc
In file included from main.cc:29:
audio.h:27:23: warning: jack/jack.h: No such file or directory
audio.h:62: error: 'jack_nframes_t' has not been declared
audio.h:82: error: 'jack_nframes_t' has not been declared
audio.h:88: error: ISO C++ forbids declaration of 'jack_client_t' with no type
audio.h:88: error: expected ';' before '*' token
audio.h:89: error: ISO C++ forbids declaration of 'jack_port_t' with no type
audio.h:89: error: expected ';' before '*' token
audio.h:90: error: ISO C++ forbids declaration of 'jack_port_t' with no type
audio.h:90: error: expected ';' before '*' token
make: *** [main.o] Error 1

========================

Both softwares semms to have a problem with jack,

Any ideas ? Anybody installed aeolus on Ubuntu ?

---

### Post by dolson on 2006-08-13
audio.h:27:23: warning: jack/jack.h: No such file or directory

That is your problem. You didn't install the development headers for JACK.

---

### Post by edev on 2006-08-14
I love those quick and easy fixes ! :D 

Thanx a lot Dolson !

---

