---
title: "RT2870 driver installed but still no internet"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by britandjack on 2010-05-13
Hiya
 
I am very new to Ubuntu and if I could get internet I'm sure I would love it as it appears very speedy! I don't want to resort to reloading Windows just because of this!
 
I've managed to install the RT2870.inf driver for my Belkin wireless adaptor but couldn't install the sys file. Hence my adaptor still won't work - well I think this is why but hoping someone can enlighten me step by step... 
 
Please could anyone help - I need exteme "muppetry" instructions 
 
Many thanks :P

---

### Post by chili555 on 2010-05-13
> couldn't install the sys file. Hence my adaptor still won't work Why couldn't you install it? I believe if the .sys is in the same folder as the .inf, that ndiswrapper will grab it. Did you try that? What does this terminal command tell us?```
dmesg | grep ndis
```Thanks.

---

