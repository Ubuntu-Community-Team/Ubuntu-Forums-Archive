---
title: "VLC + films"
date: 2008-05-21
forum: Multimedia Software
---

### Post by Kazoun on 2008-05-21
Hi,
I install Ubuntu 8.04 on my Acer 1640Z notebook all work fine :) except the external monitor. I am not able to have 2 separate monitors (like in windows) just double i.e. all information on my notebook are also on external CRT monitor. Apart from this I was happy all works fine, and then yesterday I fond out that I am not able to play films (which I was able 2 days before) with VLC. 

I thing that, I update the system when I was prompt to do, it could be due to this update?


Thank you for your help,

Kazoun

---

### Post by atomkarinca on 2008-05-21
Have you installed any codecs? If not try this first. Open up a terminal (Applications > Accessories > Terminal) and paste these commands:

```
sudo apt-get install ubuntu-restricted-extras libdvdcss2
```

now try to open those files again.

---

