---
title: "How can I use kernel 2.6.23 on 8.04?"
date: 2008-04-10
forum: Mythbuntu
---

### Post by craiga on 2008-04-10
This is probably a dumb question but I want to use 2.6.23 rather than 2.6.24

reason being is a certain application can only compile with 2.6.23 right now.

I have manged to compile it in 2.6.24 by changing the source but am getting errors

Thanks

---

### Post by superm1 on 2008-04-10
You can, but you are going to run into a lot more problems. The precompiled "extra" modules in linux-ubuntu-modules and linux-restricted-modules won't be compiled for you, and if you wanted anything in them (lirc,nvidia,fglrx,wireless,uvcvideo, ALSA), you are SOL.

Moral of the story: get your stuff to compile on 2.6.24

---

### Post by craiga on 2008-04-10
can you help me superm1?

the thing i want to compile is rather hush hush round these parts, perhaps I will wait until they get round to updateing it...yes super it is that special little proggy your thinking of....do i get banned for saying its name?

---

### Post by superm1 on 2008-04-10
Unsupported around these parts, see your sources for information on 2.6.24.

---

