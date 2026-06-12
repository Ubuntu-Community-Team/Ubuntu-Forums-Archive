---
title: "reconfigure?"
date: 2008-06-20
forum: Mandriva/Mageia
---

### Post by angry_johnnie on 2008-06-20
Is there an urpmi equivalent to dpkg-reconfigure some-package.deb?

I don't know... something like urpmi-reconfigure some-package.rpm?

And, how about a --reinstall option?

My google searches yield only similar questions :p
Is this even possible?

Thanks in advance. :-)

---

### Post by AdamWill on 2008-06-20
Erm, I don't know - what does that do?

---

### Post by pelle.k on 2008-06-21
Well, it runs (sometimes interactive) install configuration scripts supplied in the .deb package.
An example would be "dpkg-reconfigure xserver-xorg", where it helps you set up xorg.conf for you.

---

### Post by AdamWill on 2008-06-23
there's no equivalent concept in Mandriva, no. If you want to restore the original configuration for something, reinstall the package (or just get the configuration files out of it with file-roller or whatever). For the specific example, on Mandriva, you'd use drakx11 , the X configuration utility.

---

