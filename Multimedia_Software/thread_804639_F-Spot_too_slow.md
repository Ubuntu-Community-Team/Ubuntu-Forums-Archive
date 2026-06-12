---
title: "F-Spot too slow"
date: 2008-05-23
forum: Multimedia Software
---

### Post by gigenieks on 2008-05-23
Hi, guys.
I have problem with F-Spot, when I am viewing my photos and clicking **Next Photo**, it loads slow and my computer freezes or something about for a second or less... Picture appear first blury and about 2-4 sec later picture is sharp. It sharpens in pixel rows from top edge to lower edge.
I want to load more quickly my photos!:(

Any suggestions?

P.s. sorry for my bad english or termilogy

---

### Post by xc3RnbFO8P on 2008-05-23
See if you have to enable grapics driver in:
System> administration> hardware drivers

---

### Post by gigenieks on 2008-05-23
Yes I have. :)

---

### Post by xc3RnbFO8P on 2008-05-23
What are the specifications of your computer?

---

### Post by gigenieks on 2008-05-23
Intel Pentium 4 3.4ghz
nVidia GeForce 6600GT
2gb ram

---

### Post by xc3RnbFO8P on 2008-05-23
Run F-Spot from terminal:
> $ **f-spot**    <return>
See if there is a error messages when you are viewing pictures.

---

### Post by xc3RnbFO8P on 2008-05-23
Double post

---

### Post by furiousphil on 2008-07-07
I have got the same problem: Images load very very slow! It is annoying. Also the Slideshow's transition between images is done in about 2 Frames which looks terrible and slows down the viewing of pictures a lot.

I don't have these problems in gthumb, but as i like the tagging of f-spot a lot better, I would like to use f-spot.

The terminal does not give any errors and my graphics card seems to be properly installed (Geforce 5700)

Hope anyone knows what to do, thank you
Philipp

---

### Post by Dixon Bainbridge on 2008-07-07
Use a different viewer? Not trying to be flippant, but F-spot is an awful piece of software. Gnome's built in viewer is so much better, and much more responsive. Or try gwenview.

---

### Post by furiousphil on 2008-07-13
I have to admit you are right! I tested gthumb for a couple of hours and somehow got used to it. Its far from a perfect viewer and organizer but fast and slim.

---

### Post by lion99 on 2008-07-13
The problem with f-spot is that it uses Mono, which is a .Net clone, and causes a HUGE amount of libraries to be loaded. Another Mono program is Beagle, the desktop search thing. Most of us don't need M$-style bloat and bugs in out Linux systems. I can't speak for Gnome systems, but on KDE there is strigi, which is maybe a thousand times faster than Beagle, and does not need any bloated libraries.

Mono based stuff is best avoided. It is thought to be patent-encumbered, and unlike SuSE, Xandros and Linspire, Canonical have not, and as far as I can see, will not be doing a patent deal with the Evil Monopoly, so there could be legal liability in using it.

Sorry to be "political", but the technical reasons for not using Mono are quite compelling too. Over 100MB of libraries makes for one big slowdown. I have a twin core AMD64X2 4800MHz (quite old now, there are faster, but it is fully adequate for anything I do), with 4GB of RAM, and Mono brings that right down to a crawl.

I simply removed Mono and everything dependent on it, and will never, ever be using it again.

If you search with Synaptic, or Adept if you are using KDE, you should find lots of similar programs to f-spot. I seem to remember counting over 20, last time this topic arose. Some will be good, others mediocre, the choice is personal, and Linux gives you the freedom to chose what works the way you like best. Most of them will not need Mono, so should be fast. The great thing is that if you try one and don't like it, it will uninstall cleanly.

Alan

---

