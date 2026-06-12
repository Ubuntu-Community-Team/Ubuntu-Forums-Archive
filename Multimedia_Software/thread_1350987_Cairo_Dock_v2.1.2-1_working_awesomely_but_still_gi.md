---
title: "Cairo Dock v2.1.2-1 working awesomely but still giving black background"
date: 2009-12-09
forum: Multimedia Software
---

### Post by thegr81isbak on 2009-12-09
Hey all, 
I've seen some threads about the same thing , but its got different versions
Now the Cairo Dock site says that after version 2 came out the OpenGL version of Cairo Dock works properly without any of that black background problem .

Config of my laptop, Dell Studio 15 - ATI HD 4570 ( Installed the ATI/AMD Proprietary FGLRX graphics driver) - running Ubuntu 9.10 Karmic Koala and have compiz fusion setup and working just fine. 
After that i got Cairo-Dock , the latest version 2.1.2 and it works fine with all the features and the rotate and the  green lines effect when you hover over the icon with the OpenGL version - BUT there is like a big black box that take over the bottom 1/8th of the screen when it runs and the dock is resting at the bottom of the black box. This is a link to a screenshot of the dekstop when i start Cairo Dock, you can clearly see this black box covering the bottom part of the screen.
[http://img706.imageshack.us/img706/5293/screenshotx.jpg]("http://img706.imageshack.us/img706/5293/screenshotx.jpg")
If anyone can please tell me how to fix this once and for all i would appreciate it.

---

### Post by GeekPapa on 2009-12-10
I hate to "me too" here, but me too.  I basically lost all my configuration elements and can't get the corners to round on the 3D Plane

---

### Post by GeekPapa on 2009-12-14
One quick update.  I switched to the non-open-gl version of Cairo-dock and it is better.  The black box is gone.  When I hover over an icon it still eclipses windows with a "sampled" bit of background.  I am living with it for now, but would really like to get it back to the way it was.  I also switched themes and have a nice rounded corner thing going on.  I am running Metacity compositor.

---

### Post by thegr81isbak on 2009-12-14
Lol the first thing i did after i saw the black box in the open-gl version was to start the one without open gl and that works just fine as well, but after checking out the awesome effects in the open gl version i would prefer to have that instead of the one without opengl

Can someone please help us with this? :)

---

### Post by fabounet on 2009-12-15
you may have to install the latest drivers of your graphic card.
also, did you try without auto-hide ?

---

### Post by thegr81isbak on 2009-12-15
I hate to be rude, but Its not as easy a solution as that. If you read some of the other posts about the same problem you'll see it takes much more than that, but v2.0 says its been fixed but i still have the problem! Which is the whole problem!
Yeah my graphics card is up to date and yes i have tried everything possible including disabling autohide and reinstalling it twice.

---

### Post by AlanR8 on 2009-12-15
And you're SURE you have compositing enabled? If you don't like Compiz, have a look at Metacity......

---

### Post by fabounet on 2009-12-16
well some cards just don't support OpenGL correctly.
new Catalyst drivers add a correct support, but only for cards after 9600, which may not be your case.

---

### Post by thegr81isbak on 2009-12-16
Yeah  i have composting enabled and i love compiz!!

And i'm pretty sure my graphics card supports OpenGL well, i've used other programs that require it adn they work well and this Dock in itself, like i mentioend uses OpenGL to work and it works excellent with all the graphics on it, like you can in the picture, its just the black box that i don't know how to take care of

---

### Post by fabounet on 2009-12-17
```
my graphics card supports OpenGL well
```
obviously not ^_^
it supports OpenGL, but maybe not completely.
it is well-known that old ATI have crappy drivers.

---

### Post by mCion on 2009-12-18
similar problem with ATI radeon HD 4350,

For some people if you turn on the emulate fake transparency setting gets rid of the black box.:)

I got rid of that, but have a weird halo surrounding it, and also the OPenGL animations show as a white box.

Karmic, cairo 2.0.9 karmic, new computer, compiz, etc.etc

---

