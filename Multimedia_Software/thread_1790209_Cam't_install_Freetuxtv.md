---
title: "Cam't install Freetuxtv"
date: 2011-06-24
forum: Multimedia Software
---

### Post by bolkonski on 2011-06-24
Hi Guys,
I like the look of Freetuxtv and want to try it out. However, I couldn't  install it. Here's the end with failure text. I'd appreciate any help.  Best wishes
bolonski

W: Failed to fetch [http://ppa.launchpad.net/team-xbme/p...source/Sources]("http://ppa.launchpad.net/team-xbme/ppa/ubuntu/dists/natty/main/source/Sources")  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbme/p...-i386/Packages]("http://ppa.launchpad.net/team-xbme/ppa/ubuntu/dists/natty/main/binary-i386/Packages")  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
steve@:~$ sudo apt-get install freetuxtv
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package freetuxtv

---

### Post by jerrrys on 2011-06-25
[INDENT]sudo add-apt-repository ppa:freetuxtv/freetuxtv
 sudo apt-get update
 sudo apt-get install freetuxtv
[/INDENT]

---

### Post by bolkonski on 2011-06-26
Thanks for your help jerrys. I got this meassage and didn't install anything.

Fetched 11.4 kB in 3s (2,984 B/s)
W: Failed to fetch [http://ppa.launchpad.net/team-xbme/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/team-xbme/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbme/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/team-xbme/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by jerrrys on 2011-06-26
in 'software sources', change your server or select the 'find best server' option

---

