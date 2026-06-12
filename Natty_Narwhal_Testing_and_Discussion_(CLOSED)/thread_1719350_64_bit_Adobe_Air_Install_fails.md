---
title: "64 bit Adobe Air Install fails"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by WeeDavey on 2011-04-01
Trying to install 64 bit Adobe Air (download bin file from Adobe site) but get msg
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64
Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

Install does continue to the Adobe licence agreement window but at that point I cancel as not convinced all will be well.
Anyone had similar ?

---

### Post by tgalati4 on 2011-04-01
I was under the impression that Adobe Air was only 32-bit.  Did you find a 64-bit version?  If so, then it looks like you have a 32-bit version of a gtk widget (libappmenu.so).

---

### Post by graphius on 2011-04-25
> **tgalati4 said:**
> I was under the impression that Adobe Air was only 32-bit.  Did you find a 64-bit version?  If so, then it looks like you have a 32-bit version of a gtk widget (libappmenu.so).
This worked for me, thanks...

---

