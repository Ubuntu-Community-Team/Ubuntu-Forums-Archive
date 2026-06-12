---
title: "How can you tell which video driver is being used?"
date: 2009-03-13
forum: Multimedia Software
---

### Post by timzak on 2009-03-13
With the new xorg.conf files, everything is automatically detected.  How can one find out which video driver xorg picked?  

I'm using an old PCI video card and want to know if the vendor-specific driver is being used, or if the generic VESA driver is being used.

Thanks.

---

### Post by wolfen69 on 2009-03-13
if you did not install a video driver yourself, you are using the default open source driver. do:
```
lspci
``` to see what card you are using.

---

### Post by timzak on 2009-03-13
> **wolfen69 said:**
> if you did not install a video driver yourself, you are using the default open source driver. do:
```
lspci
``` to see what card you are using.

Okay, I just wanted to make sure the generic VESA driver wasn't being used in place of the open source, chipset-specific driver.

Would lspci tell me if the VESA driver were being used?

---

### Post by markbuntu on 2009-03-13
No, lspci will not tell you that but you can look in /var/log/Xorg.0.log and that will tell you.

---

### Post by timzak on 2009-03-13
> **markbuntu said:**
> No, lspci will not tell you that but you can look in /var/log/Xorg.0.log and that will tell you.

Thanks, it appears the video chipset's driver is being used.  For those who remember this one, it's the original Matrox Millennium.  MGA2064W.  High end for the day.

---

