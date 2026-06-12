---
title: "Radeon anti-aliasing?"
date: 2005-12-04
forum: Multimedia &amp; Video
---

### Post by Fredric on 2005-12-04
I managed to get my laptop's graphics card working correctly, with 1000 fps in flgrxgears.  This is great because I'm going in for an important job interview in a few weeks as a graphics programmer, and I would like to show some examples of what I've done on the laptop..

The problem is that I can't get anti-aliasing to work with the Radeon card.  I have tried setting the FSAAEnable and FSAAScale values, as is said in the how-tos, but the jaggies are still there.  Is there something that I'm missing?

-Fredric

---

### Post by caravel on 2006-10-17
I'm not too hot on this myself, but there should be something like this in your xorg.conf:

Option "FSAAEnable" "no"
Option "FSAAScale" "1"

I expect you'd have to change that from "no" to "yes" to turn on FSAA.

Which driver did you install?

---

### Post by bewire on 2006-10-17
> **caravel said:**
> I'm not too hot on this myself, but there should be something like this in your xorg.conf:

Option "FSAAEnable" "no"
Option "FSAAScale" "1"

I expect you'd have to change that from "no" to "yes" to turn on FSAA.

Which driver did you install?

Hi, can you please provide xorg.conf ? I don't have refrences to anything related FSAA* in mine, but are experiencing the same problem on mye desktop ...

bewire

---

