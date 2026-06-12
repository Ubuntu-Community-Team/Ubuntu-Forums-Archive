---
title: "How to tell which graphics driver I'm using?"
date: 2010-05-15
forum: Multimedia Software
---

### Post by timkoop on 2010-05-15
Does anyone know how to find out which graphics driver Ubuntu is using?

I can use lspci to find out what hardware is there, but how do I know which driver is controlling it?

Thanks.

--
Tim

---

### Post by Praetor77 on 2010-05-15
Check your xorg logs for:

(II) LoadModule: "fbdev" or
(II) LoadModule: "intel" or
(II) LoadModule: "vesa" ...etc.

---

