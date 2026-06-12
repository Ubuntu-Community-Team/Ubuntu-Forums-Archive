---
title: "Ubuntu 12.10 Video Driver Toshiba"
date: 2012-10-21
forum: Multimedia Software
---

### Post by jonburton on 2012-10-21
Hi,

I am running Ubuntu 12.10 on a Toshiba R840 laptop that I believe is one of the few certified for Ubuntu. However when I go to system details it says in Graphics. driver unknown, experience standard.

I was hoping this machine would give me a full Ubuntu experience. Anyone any ideas please?

The spec of my laptop is here- [http://uk.computers.toshiba-europe.com/innovation/product/Tecra-R840-11E/1105435/toshibaShop/true/](http://uk.computers.toshiba-europe.com/innovation/product/Tecra-R840-11E/1105435/toshibaShop/true/)

---

### Post by jonburton on 2012-10-21
Ive just checked and the graphics card is an Intel 3000 HD if that helps diagnose the issue?

Thanks

---

### Post by PippoPalmieri on 2012-10-21
Hello there,
I had the same issue. I believe your graphic card is properly recognized and used, it's just that it's not displayed in the system information.
Try from terminal:

> sudo apt-get install mesa-utils


Then check again, it should be displayed

---

### Post by jonburton on 2012-10-21
Thanks, Its now saying Intel Sandybridge mobile with an experience of Standard.

Is that correct? Is there an "advanced" experience?

---

### Post by PippoPalmieri on 2012-10-21
As far as i know, there's no advanced experience. It only notices you when you're either in fallback mode, or when it correctly uses your drivers (standard).

---

### Post by Linuxisfast on 2012-10-21
Ignore that, I get the same message here and my graphics are Intel 3000HD as well, just make sure to install the intel-vaapi package to get full HD movies to play.

---

