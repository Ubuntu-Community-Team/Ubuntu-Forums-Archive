---
title: "Integrated Intel G45 graphic not working?"
date: 2010-01-10
forum: Multimedia Software
---

### Post by Turin Turambar on 2010-01-10
I can only log into X with "vesa" driver (otherwise it gives me the black screen) and ubuntu never boots directly into GDM, always the console. 

Any hint or info what to do?

I'm using ubuntu koala. Thanks.

---

### Post by Turin Turambar on 2010-01-12
The problem was in the (stupid) BIOS setting.
Apparently, "first VGA initialization " was set to "onboard" (which is normal if you don't have other vga card). However, you need to set it to "PCI" if you don't want Ubuntu to crash.

---

