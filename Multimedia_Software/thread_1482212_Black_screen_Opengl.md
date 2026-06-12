---
title: "Black screen Opengl"
date: 2010-05-13
forum: Multimedia Software
---

### Post by zather on 2010-05-13
im new to ubuntu and want to use my 4870 x2 to like play dolphin (Wii emu)
but when im on opengl its just a black screen and if i change to software its ok but
the fps is like 2 fps and on opengl its 60 all the time, so i really want to use opengl.
Some1 that knows how to fix it?

---

### Post by Mugatu on 2010-07-05
I had the same problem.  Running these commands in a terminal fixed it for me:

```
wget https://launchpad.net/~glennric/+archive/dolphin-emu/+files/nvidia-cg-toolkit_2.2.201002-0ubuntu1~lucid_amd64.deb
sudo dpkg -i nvidia-cg-toolkit_2.2.201002-0ubuntu1~lucid_amd64.deb
```

Edit:
It just occurred to me that those instructions are specific to Ubuntu 10.04 64-bit.  Something like this is possibly better:

```
sudo add-apt-repository ppa:glennric
sudo aptitude update
sudo aptitude safe-upgrade
```

(this should upgrade nvidia-cg-toolkit and probably dolphin-emu as well)

---

