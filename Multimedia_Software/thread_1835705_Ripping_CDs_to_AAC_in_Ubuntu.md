---
title: "Ripping CDs to AAC in Ubuntu"
date: 2011-08-29
forum: Multimedia Software
---

### Post by lalilulelo on 2011-08-29
I'd like to be able to rip CDs to AAC files in Ubuntu, but I'm having some difficulty. Banshee will not rip to AAC at all. Sound Juicer will, but I have some problems with it. Firstly, there doesn't seem to be a way to control the bitrate at which it encodes the AAC files. It apparently rips them at 128kbps automatically, although I'd like them to be 256kbps. Secondly, when I open these files in Banshee, a lot of the metadata is missing, such as the artist name.

Any thoughts as to how I may be able to solve any or all of these problems?

By the way, I'm using Ubuntu 11.04.

---

### Post by zeroseven0183 on 2011-08-29
Try it using K3B. I haven't used Banshee and Sound Juice to rip CDs but K3B, I believe, can do it for you.

---

### Post by ron999 on 2011-08-29
> **zeroseven0183 said:**
> Try it using K3B.
Yes, **K3b** and **RubyRipper** will both rip CDs to aac using **neroAacEnc** encoder and **neroAacTag** tagger.
But they don't do it straight out of the box, needs some extra work.:cool:

---

### Post by lalilulelo on 2011-08-29
Cool. Can you point me in the direction of a guide on how to do that in Ubuntu? I found some, but they appear to be for other versions of Linux.

---

### Post by andrew.46 on 2011-08-30
abcde should be able to do this, a sample ~/.abcde.conf here:

[http://www.andrews-corner.org/abcde.html#aac](http://www.andrews-corner.org/abcde.html#aac)

---

