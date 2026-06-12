---
title: "beginner help for GIMP ?"
date: 2011-03-15
forum: Multimedia Software
---

### Post by Adbru on 2011-03-15
Hello,

Forgive me if this is the wrong place, (mods please move this if required )

I have never really used GIMP before but I currently have a very specific need that I hope someone can help me with.
It sounds simple but i havent found the right way to do it yet !

As part of my uni work I want to be able to add a colour filter/overlay to an image.
Similar in idea to looking at the image through a coloured lens.
I also want to be able to alter the colour of the 'filter'

The idea is to assist people who have a colour vision deficiency (colour-blind).

I currently have Gimp v2.4.6 on my pc.

Many thanks in advance for any help or pointers :)

Adbru

---

### Post by mcduck on 2011-03-15
The easiest way to do that is this:

1. Add a new layer above your image layer), and set it's mode to "Multiply"

2. Fill the layer with the desired color (using the Bucket Fill Tool)

Now all you need to do to change the color is to use the Bucket Fill Tool again to fill the layer with another color.

You could also try the "Overlay" mode instead of "Multiply", but "Multiply" is really the one that behaves like an actual photo filter would.

---

### Post by Adbru on 2011-03-16
Hi McDuck,

Thanks for the reply, that looks like what I need :-)

Regards

Adbru

---

