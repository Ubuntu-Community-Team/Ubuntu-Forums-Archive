---
title: "[SOLVED] how do you load cinelerra?"
date: 2008-07-31
forum: Multimedia Software
---

### Post by harryliddic on 2008-07-31
I have tried all evening to load cinelerra? I been through mirror sites, and do loops but I haven't found one site where clicking a cursor that will give me the source code  or a tar ball that I can download and build the program or even a LIVE DVD.

---

### Post by Tree MendUs on 2008-07-31
1) Instructions for for Cinelerra CV (Community Version) at;
[http://cinelerra.org/getting_cinelerra.php](http://cinelerra.org/getting_cinelerra.php)
This is amongst the best ways of installing cinelerra.

2) Cinelerra (Heroine Virtual Version) available at;
[http://heroinewarrior.com/download.php3](http://heroinewarrior.com/download.php3)

But this is source code, which needs compiling, so not for newbies.

3) Could also look for a recent RPM version, and use "alien" to convert it to a "deb" file for installation. (just click on the deb file to open up the deb installer.)

---

### Post by Erlander on 2008-07-31
Try This:

[http://ubuntuforums.org/showthread.php?t=464223](http://ubuntuforums.org/showthread.php?t=464223)

Rob


Edit:  It is also in the repositories so Synapatic can be used.

---

### Post by roaldz on 2008-07-31
[http://akiradproject.net/repository](http://akiradproject.net/repository)

scroll down, look at the black boxes

---

### Post by harryliddic on 2008-07-31
what black boxes?

---

### Post by roaldz on 2008-07-31
Those which contain this:

for Hardy:
```
sudo wget http://akirad.cinelerra.org/dists/hardy.list -O /etc/apt/sources.list.d/akirad.list
wget -q http://akirad.cinelerra.org/dists/akirad.key -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by harryliddic on 2008-07-31
sorry I was looking in the Synaptic. very thing worked fine its downloading now. Thanks for your help and sorry for my stupidity.

---

