---
title: "can i use windows drivers for my soundcard with wine?"
date: 2009-01-06
forum: Multimedia Software
---

### Post by killbydemons on 2009-01-06
Just wondering if I can use Wine to run windows drivers for my Soundblaster X-Fi card.  It isn't supported in ubuntu, but using Wine, could I install a windows driver to use my soundcard in windows games?

I just don't want my soundcard to be useless now because it isn't supported in ubuntu :(

---

### Post by binbash on 2009-01-06
as far as i know you cant use it

---

### Post by maestrobwh1 on 2009-01-06
I am quite sure it is a no go.  Wine does not work that way.  I don't know enough to explain why not in real technical details, but I just know that wine can't use win drivers because of the way it interacts with Linux and your hardware: it doesn't.  

If you have a soundcard, and ALSA can see the sound card, then Wine can use ALSA.  You could not install a windows printer driver through wine for the same reason.  Wine communicates with the Linux driver, CUPS, not the hardware itself.

---

### Post by killbydemons on 2009-01-06
awww, oh well it was worth a shot. maybe they'll have X-fi compatibility in the future?

---

