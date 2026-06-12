---
title: "Xsane not available anymore in Gimp 2.10"
date: 2022-04-23
forum: Multimedia Software
---

### Post by Hagar Delest on 2022-04-23
Hi All,

Several discussions on the net but no answer found yet...
Fresh install of Xubuntu 22.04, fresh profile of Gimp 2.10 and Xsane 0.999 installed as well.
The device dialog option in File > Create is no longer there. It did that for some time already (Xubuntu 21.10 and may be before).
It seems to be linked to Gimp 2.10 but not sure.

I can't believe no one has come with a fix or at least an explanation.
Any hint?

Notes:
- I can run Xsane and save the pic before opening it in Gimp but it used to be easier with the plugin integration.
- When opening Gimp for the first time (new profile), it shows that it is interrogating xsane plugin (for quite some time BTW) but then nothing.

---

### Post by mandofab2 on 2022-11-08
Me too

Tried with 2.10.30, 2.10.32 and the developer beta version - no 'Create from scanner' option. Got a feeling this is a regular problem with GIMP

---

### Post by Holger_Gehrke on 2022-11-08
You could try installing the package 'sane'. This includes 'xscanimage' which can be used by GiMP. Works for me on XUbuntu 22.04 with Gimp 2.10.30.

Holger

---

### Post by Hagar Delest on 2022-11-08
Excellent, you're a lifesaver Holger!
Using sane instead of xsane did the trick.
Many thanks!

---

