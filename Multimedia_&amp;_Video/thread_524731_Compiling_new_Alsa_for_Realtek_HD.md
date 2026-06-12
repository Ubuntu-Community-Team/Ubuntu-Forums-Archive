---
title: "Compiling new Alsa for Realtek HD"
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by unknownm on 2007-08-13
well i'm new at linux so please tell me how to do this. The current Alsa doesn't work with my hardware so I read up on a forum that you need to upgrade it to make it work

I got the 3 downloads to upgrade my alsa to use my Realtek HD. When I first do the ./config on the folder I got a error. My friend the_jester told me to get sudo apt-get gcc. I did that and I still got the same error. Can anyone give me tips on how to compile stuff like this?


Look at my picture

---

### Post by kellemes on 2007-08-13
Anything interesting in config.log?

---

### Post by unknownm on 2007-08-13
I don't even see it inside the folder.

Anyways i'm very very new to linux so sorry if I mite sound like a noob:lolflag:

---

### Post by kellemes on 2007-08-13
try **sudo** ./configure

---

### Post by kellemes on 2007-08-13
sudo updatedb
locate config.log

this will give you the location of config.log

---

### Post by unknownm on 2007-08-13
> **kellemes said:**
> try **sudo** ./configure

gah :(

> matt@matt-desktop:~/Desktop/alsa-driver-1.0.14$ sudo ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
matt@matt-desktop:~/Desktop/alsa-driver-1.0.14$ 

---

### Post by unknownm on 2007-08-13
> **kellemes said:**
> sudo updatedb
locate config.log

this will give you the location of config.log

it was in trash :S.. Anyways here is the file

---

