---
title: "graphics driver"
date: 2013-03-14
forum: Multimedia Software
---

### Post by bsufan79 on 2013-03-14
Hello everyone,

I am new to Ubuntu, my IT office is in the process of switching from MS to Ubuntu, and I am having problems installing the graphics driver on one of the machines. It is a Pentium 4 HT 3.2 dual core. I tried the command Jockey-KDE but I can't seem to get it to work. Can anyone please point me in the right direction? 

Thank you,

bsufan79

---

### Post by ManamiVixen on 2013-03-14
What Ubuntu version and what graphics card does the computer have?

---

### Post by bsufan79 on 2013-03-14
We are using Ubuntu 12.10 and the graphics card is stock with the machine. It's an old IBM 8183 DRU

---

### Post by ManamiVixen on 2013-03-14
The issue is that the computer has a chipset that Intel ceased support on in terms of graphics support, the i865G. You'll need to get a graphics card for it or go low graphics mode in VESA which has no acceleration and can only run desktops like LXDE or XFCE in no compositing mode. If the only PCI slot in the computer isn't used, you can install a card there. But it has to be a recent one, like [http://www.newegg.com/Product/Product.aspx?Item=N82E16814187194](http://www.newegg.com/Product/Product.aspx?Item=N82E16814187194) as a suggestion.

---

### Post by bsufan79 on 2013-03-15
Thank you

---

