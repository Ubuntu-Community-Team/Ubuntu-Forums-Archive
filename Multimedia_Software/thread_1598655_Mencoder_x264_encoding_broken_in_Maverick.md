---
title: "Mencoder x264 encoding broken in Maverick?"
date: 2010-10-16
forum: Multimedia Software
---

### Post by tristan on 2010-10-16
Hi all

I recently upgraded to Maverick and am loving it. Converting over my various scripts to work on the new box I notice that my video trascoding script, which uses mencoder to re-encode video as h264, now does not work.

```
mencoder $inpfile -oac mp3lame -lameopts vbr=3:q=3 -ovc x264 -x264encopts crf=22:threads=auto:subq=4:bframes=2:b_pyramid:weight_b:turbo=1 -ofps 25 -o $outfile
```

For a long time this has worked just fine but the command basically bombs out every time with 

```
FATAL: Cannot initialize video driver.
```

I tried using the medibuntu mplayer/mencoder but still no dice.

Does anyone know how I can get this important functionality back? Thanks!

---

### Post by Yellow Pasque on 2010-10-16
Ok, so what video card and driver do you have? Post /var/log/Xorg.0.log if possible.

---

### Post by tristan on 2010-10-16
> **Temüjin said:**
> Ok, so what video card and driver do you have? Post /var/log/Xorg.0.log if possible.

It's not card related I'm pretty sure, I get the same behaviour on my Acer Aspire netbook and my desktop with a GTX460.

Try the command on your box and see how you go...

---

### Post by tristan on 2010-10-17
Did a bit of playing and found out that the option **b_pyramid** has changed with recent mencoder builds. I used **b_pyramid=normal** and all is good again.

---

### Post by andrew.46 on 2010-10-20
Hi tristan,

> **tristan said:**
> Did a bit of playing and found out that the option **b_pyramid** has changed with recent mencoder builds. I used **b_pyramid=normal** and all is good again.

More recent builds of MEncoder make x264 encoding even easier by using presets, you would need to build your own though I suspect. Typical syntax is suggested here:

[http://ubuntuforums.org/showpost.php?p=9934481&postcount=1351](http://ubuntuforums.org/showpost.php?p=9934481&postcount=1351)

Andrew

---

