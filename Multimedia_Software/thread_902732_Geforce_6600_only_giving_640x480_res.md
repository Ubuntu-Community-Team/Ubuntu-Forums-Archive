---
title: "Geforce 6600 only giving 640x480 res"
date: 2008-08-27
forum: Multimedia Software
---

### Post by jcr1 on 2008-08-27
help!

New to this...I have installed a new graphics cardm nvidia geforce 6600.

I tried the standard ubuntu restricted driver, no good. I tried the nvidia website driver, (complicated) no good. I tried envyng, no good.

The best I have is 640x480. Its as if it isn't detected what monitor i have plugged in. Its a 1920x1080 lcdtv by the way, so i would expect a little more than 640x480. the same happens if i plug in a regular crt monitor too.

What the hell is going on...how do i make this work?

Cheers in advance.

---

### Post by prshah on 2008-08-27
> **jcr1 said:**
> 
New to this...I have installed a new graphics cardm nvidia geforce 6600.


Press Alt+F2, then give the command```
gksudo displayconfig-gtk
```, then check the "Graphics Card" tab; what driver does it seem to be using?

---

### Post by jcr1 on 2008-08-27
currently:

vesa - generic vesa-compliant video cards.

the last thing i did was enable the restricted driver and reboot. during reboot i had the warning box saying running in low res mode, configure. I just continued.

i can look in the lit of available drivers and see nvidia and another nvidia.

---

### Post by jcr1 on 2008-08-27
getting really hacked off now. This is even making me get fed up of Ubuntu altogether. Although there's always comments about loads of support for everything, sometimes, thing just seem like far too much hard work, when you know in the back of your mind 'this would just have worked in windows'... i dont want to feel like this!

---

