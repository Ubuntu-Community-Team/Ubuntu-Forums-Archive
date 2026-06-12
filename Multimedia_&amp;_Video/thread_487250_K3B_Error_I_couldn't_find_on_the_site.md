---
title: "K3B Error I couldn't find on the site"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by lsutiger on 2007-06-28
I am getting the following error when trying to rip to MP3 from K3B:
```
Command Failed:lame -h --tt<name of song> --ta <Name of Artist> --tl <Name of album> --ty <Year> --tc <Name of folder/track filename>
```

There is one strange thing in the Name of folder string. It is in this format:
```
/home/username//blah-blah-bah
```
As in two forward slashes after user name.
Any ideas?
Thanx in advance!

---

### Post by lsutiger on 2007-06-29
Bump

---

### Post by yabbadabbadont on 2007-06-29
Do you have lame installed?

---

### Post by lsutiger on 2007-06-29
yeppers!

---

### Post by yabbadabbadont on 2007-06-29
How about the mp3 k3b plugin?  I don't remember the package name.  Use synaptic to search for k3b in the package name and you should see the one that I'm talking about.

---

### Post by lsutiger on 2007-06-30
I did a search of "mp3 k3b plugin" and one library came up, libk3b2-mp3, and I have it installed. The error seems to be in the filename.
This is what I have for the external audio encoder configuration:```
lame -h --tt %t --ta %a --tl %m --ty %y --tc %c - %f
```

---

### Post by lsutiger on 2007-07-01
Bump

---

### Post by lsutiger on 2007-07-03
bump

---

### Post by lsutiger on 2007-07-10
bump

---

### Post by cold_light on 2007-08-23
I had the exact same problem.

try this:
```
sudo apt-get install lame
```

Obviously, close/open K3B.

Erm. Yeah.
Bye.

---

