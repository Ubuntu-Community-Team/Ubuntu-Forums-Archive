---
title: "How can i tell what video driver Ubuntu 9.04 is using"
date: 2009-05-20
forum: Multimedia Software
---

### Post by hatewindows on 2009-05-20
and can i change the driver? I have a dell GX 280 using an intel chip set.. thanks!!  MARK

---

### Post by khelben1979 on 2009-05-20
Does that mean it's using integrated graphics which sits on the motherboard?

If you have a graphics card on it, this will output the data related to it: ```
sudo lspci | grep VGA
```

---

