---
title: "Screen color calibration"
date: 2013-12-14
forum: Multimedia Software
---

### Post by Da_Panther on 2013-12-14
Hey, 

I've been reading and reading and reading ...... and I just can't find the answer.

I have a Macbook 4,1 (late 2008) and I absolutely cannot stand the color profile anymore, after running Ubutu for two years. The colors are not well calibrated. The white temperature, for one, is 6500K and I would like to bring it down to 5000K.

I have tried different applications to try to calibrate my screen, but nothing works. 

In OS X< there is the color profile management application where you can manually and step-by-step modify the color output on the screen. I have found one application for Linux that can do this -- Color Manager. However, to calibrate the screen, it requires a photometric device, which I am not interested in purchasing.

Can anybody point me to a graphical application that gives me the ability to permanenty apply a color calibration to my laptop screen? I am desperate. Thanks!!

---

### Post by tgalati4 on 2013-12-14
I believe you can copy the *.icc profile from the mac side to the linux side.  You just have to find it and put it in the correct directory.  I agree, the mac has a nice color calibration tool.  To write a similar tool in linux would require open source knowledge of the graphics card--something that is elusive with high-end graphics chips.  The photometric tool is simply a light meter.  I'm surprised that one hasn't been written for an Android phone to use as a light meter for such calibration.

[https://help.ubuntu.com/community/MacBookPro7-1/Lucid#Screen](https://help.ubuntu.com/community/MacBookPro7-1/Lucid#Screen)

---

### Post by Da_Panther on 2013-12-14
omgomgomgomgomgomgomg....... OMG~!!! I would kiss you.

Its done. It works. I tried importing other ICC profiles, but I guess they just weren't the right standard or whatnot.

Thank you. so much.

---

### Post by tgalati4 on 2013-12-14
You can create several profiles on the mac--just give them different, descriptive names.  Then use the Color Manager to import them as needed for different use cases.  Watching movies would be a different color profile than editing photos, etc.  Stock profiles probably won't work, because the mac has a very detailed profile map, so just recreate them using the mac tool.

I will go find some mistletoe.

How about a Haiku instead:

Color Profile woes?
Make and copy ICC.
No more color blues.

---

