---
title: "ATI HD7850 driver issue"
date: 2012-04-03
forum: Multimedia Software
---

### Post by Siebert on 2012-04-03
Dear community,

I am quite new to Linux, that is why I chose Ubuntu :) because configuring drivers over the terminal is not one of my strengths, yet, in other words a PITA for me. I had a 3870 before and exchanged it with the 7850, naively thinking that the installed Catalyst driver should at least handle my new card, but fail ... the gnome-GUI would not open after booting, and manually trying to open it with "startx" lead to errors in the xorg.conf. So my question is, do I have to install the new Catalyst, and primarily how I can install it via commands in the terminal. Sorry if this question was asked a million times before but I need to be sure, that my card is supported at least. Otherwise I will install a completely new distro (have 11.10 64 it atm, 2 monitors).

Thanks for the help and kind regards,

S.

---

### Post by QIII on 2012-04-03
When you installed the driver, did you do 

```
sudo aticonfig --initial
```

?

---

