---
title: "Which Graphics card? Geforce fx 5200 or Asus n6200?"
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by terryeden on 2006-06-08
Afternoon all,

A friend gave me two unused graphics cards as I'm currently running on my motherboard's built in graphics.

The cards are
NVidia Geforce FX 5200
Asus N6200.

I've three questions
1) Which is the better card in terms of Linux support?

2) Which is the better card in terms of speed, polygons etc?

3) How do I install them? I know how to rip the case off my box etc - but in Windows I'd plug in the new card, switch on the machine and it would get the drivers automagically.  Will Ubuntu do that?

Thanks for your help!

T

---

### Post by localzuk on 2006-06-08
I would go for the 6200 IIRC... Support is the same (both use the same drivers). You will likely have to run 'sudo dpkg-reconfigure xserver-xorg' from the console (as the screen will likely not *just work* and will drop you to the console.

---

### Post by christhemonkey on 2006-06-08
If your only going to be using one, i can give the other a good home....:D

As to the other one, plug it in, switch pc on.
Then press Ctrl+Alt+F1, and type:
```
sudo /etc/init.d/gdm stop
```

Then;
```
sudo vi /etc/X11/xorg.conf
```
Locate the section refferring to the graphics card,
Change the line where it says driver     nv (may not say nv) to
```
driver           vesa
```

Then type:

```
sudo /etc/init.d/gdm start 
```

Hopefully, that will give you basic GUI.

---

