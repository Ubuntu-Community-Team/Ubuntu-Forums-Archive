---
title: "? livecd wireless"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by amurphy96822 on 2009-03-16
HI:  simple question: I am considering installing ubuntu (either the 8.10 or the previous) as double boot on my HP Pavillion laptop. I have checked your list of compatible wireless cards and learn that my Intell Pro should work "right out of the box";  however it clearly does not work from the live cd.  Do I have to install ubuntu (writing over my quite good PCLinux OS) for it to work?  This ia a little scary.  If that is the case, you should take a look at the PCLinuxOS live cd inwhich the wireless works great without having to install.  thanks

---

### Post by ugm6hr on 2009-03-17
Most Intel cards do work out of the box, even on a LiveCD.

If it works with PCLOS, the likelihood is it will work with Ubuntu.

Do you "see" any networks with the Ubuntu LiveCD?

You can give more detail with:
```
lspci
lshw -class network
```

---

