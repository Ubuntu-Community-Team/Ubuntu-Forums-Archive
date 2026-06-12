---
title: "installing withought internet connections"
date: 2008-05-12
forum: Multimedia Software
---

### Post by vikasmk on 2008-05-12
Ok, I talked my friend into installing linux, he installed hardy and is impressed with it, but since totem player doesn't have many codecs he cant play many formats . since he doesn't have an internet connection how can he install lets say VLC on his system , I have an internet connections can i download it and install it on his system , if so how?? thanx in advance

---

### Post by pytheas22 on 2008-05-12
Individual packages can be installed by downloading them at packages.ubuntu.com and transferring them to the machine without an Internet connection.  This can be a hassle, however, for packages that require a lot of dependencies.

A solution that's probably easier is to use [APTonCD]("http://aptoncd.sourceforge.net/") to create a mirror of an online repository on a CD and give that to your friend.  You could also use this utility to create a copy of all of the packages on your system, which probably already has vlc, codecs and other important software, and give them to your friend.

There's also a more advanced guide to mirroring repositories on removable media at [http://howtoforge.com/dvd_images_of_ubuntu_repositories](http://howtoforge.com/dvd_images_of_ubuntu_repositories) .

---

### Post by vikasmk on 2008-05-13
i'll try that one out and get back at you :)

---

### Post by vikasmk on 2008-05-13
i tried aptoncd and it works very  well, thanx......:)

---

