---
title: "hevc x265"
date: 2016-01-21
forum: Multimedia Software
---

### Post by jerry50 on 2016-01-21
I have VLC version 2.1.6 Rincewind and it won't play HEVC x265 file.  What do I need to do?  Step by step...like I'm an 8 yr. old, please.

---

### Post by mc4man on 2016-01-21
Should work with most hevc files - 
```
sudo add-apt-repository ppa:strukturag/libde265
```
```
sudo apt-get update
```
```
sudo apt-get install vlc-plugin-libde265
```

ppa main page - [https://launchpad.net/~strukturag/+archive/ubuntu/libde265](https://launchpad.net/~strukturag/+archive/ubuntu/libde265)

---

### Post by jerry50 on 2016-01-21
Thanks for the help.

---

