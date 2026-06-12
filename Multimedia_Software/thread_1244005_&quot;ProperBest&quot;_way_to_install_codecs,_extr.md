---
title: "&quot;Proper/Best&quot; way to install codecs, extras, etc?"
date: 2009-08-19
forum: Multimedia Software
---

### Post by virtualu2 on 2009-08-19
Hi,
I have read a bunch of threads on getting media to play, mp3, dvd's, backup of movie dvd's, etc.  I read about the medibuntu package, just installing items separately, etc.

What is the best way to add in all the items to play restricted formats, backup my movie dvd's, etc?

---

### Post by stinger30au on 2009-08-19
dunno about the best way, but heres how i do it

follow this for what ever version your using

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

then to setup all the codecs u need do this

sudo apt-get install libdvdcss2

also

sudo apt-get install w32codecs (if u are using 32 bit cpu)

or

sudo apt-get install w64codecs (if using 64 bit cpu)

also

sudo apt-get install non-free-codecs

also

sudo apt-get install ubuntu-restricted-extras (if using ubuntu)

also
sudo apt-get install k9copy

(lets u rip dvds)

once this is done, restart pc

make sure you can play a dvd and if it can play fine, then u can rip till your hearts content using k9copy

---

