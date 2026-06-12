---
title: "Any help getting wireless to work without having a wired connection"
date: 2010-09-15
forum: Networking &amp; Wireless
---

### Post by mickey12gauge on 2010-09-15
I have absolutely no way to hook my netbook up to a wired connection and was hoping somebody could explain to me, if at all possible, how to set up internet access on my netbook.

HP mini 110 

:popcorn:

---

### Post by chili555 on 2010-09-15
It depends on the type of wireless card and if we need to grab some drivers off the internet on another computer and transfer them on a CD or USB drive. Let's start by asking the computer what kind of wireless card it has. Please open Applications > Accessories > Terminal and input:```
sudo lshw -C network
```That means, "list the hardware of the class 'network.'" Post the information related to your wireless card and we'll get started.

---

