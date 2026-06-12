---
title: "Black and White TV out put"
date: 2008-06-06
forum: Multimedia Software
---

### Post by ultraloveninja on 2008-06-06
HI!
I have a nVidia GeForce 7300 LE with a S-video out.

I have 8.04 installed with the new nVidia drivers running.

However when I connect to my TV and enable, it comes out black and white.

I am converting it from s-video to RCA (composite).  I am not sure if that is causing it or not.  (sorry I am still old school and my TV doesn't have an s-video input on it).

There is no setting to change the output to anyting else in the nVidia X server settings.

Any ideas (a side from getting a new TV)...?

---

### Post by Erlander on 2008-06-07
It could be a mixup between PAL and NTSC.

Check that your settings are correct for which ever video standard you should be using.

Rob

---

### Post by pk386 on 2008-06-07
You may want to try another S-vid to Composite (RCA) adapter...

S-video has 4 wires/ 2 pairs 

Pair 1 = chroma = Color
Pair 2 = Lumen essence = Brightness

you may be missing pair 1

[http://en.wikipedia.org/wiki/Svideo]("http://en.wikipedia.org/wiki/Svideo")

I think your adapter may be broken

---

### Post by mastermindg on 2008-06-07
Also, if the adapter doesn't solve this try installing the envy drivers -

nvidia-glx-new-envy

This is supposed to have better support for TV-out.

Good luck.

---

### Post by ultraloveninja on 2008-06-08
sweet.  thanks for the input.
i'll mess around with it today.

i'll let ya'll know if I find anything.

---

### Post by Tom Mann on 2008-06-08
nVidia cards default to s-video out, which is not the same as composite. you need to add a line to the device section of your xorg.conf (or edit as necessary) so you have a line like:

Option "TVOutputFormat" "Composite"

(I think it is as above anyway)

that should make the difference when you hit an X screen. Good luck!

---

