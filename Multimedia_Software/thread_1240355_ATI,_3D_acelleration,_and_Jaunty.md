---
title: "ATI, 3D acelleration, and Jaunty"
date: 2009-08-14
forum: Multimedia Software
---

### Post by rfLarke on 2009-08-14
Hey guys. I own a Compaq Presario V5000 with an ATI Radeon 200M (I *think*) and what with all of the lack of certain proprietary drivers and such, I'm a bit limited with my graphics card.

To put it simply, I installed "Glest" the other day, and it looks pretty awesome. Unfortunately, it barely runs worth anything on Ubuntu because I hardly have any support for 3D, it would seem. I can't seem to find any other drivers besides the default Open Source, and fglrx (So please tell me if I'm missing out on something) and installing fglrx makes Ubuntu freeze at bootup.

So if anyone knows how to have good 3D support on my machine, please tell me.

Also, if anyone knows how/if it's possible to run fglrx?

Thanks
  -rf

---

### Post by whisp71 on 2009-08-14
Check amd.com for appropriate drivers for your card.

Jaunty installs pretty old ATI drivers by default (9.3), and it's known for instability. Refer to this manual:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide) to install last ones.

---

### Post by rfLarke on 2009-08-14
After some more research, I've come under the impression that even 9.3 isn't even compatible with the current version of XORG..?

---

### Post by markbuntu on 2009-08-14
No no no. Do not install the proprietary driver with that card. If you have installed fglrx remove it.

You should be using the open source ati or radeon driver. 

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by rfLarke on 2009-08-14
Well, either way, following the instructions on [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) doesn't seem to do me any good.

So am I basically stuck without decent 3D support?

---

### Post by whisp71 on 2009-08-14
Considering your card model - yes

---

### Post by rfLarke on 2009-08-14
I see.. In that case, would it be practical to downgrade XORG/whatever it takes to be able to use fglrx? If so, how would I go about it?

---

