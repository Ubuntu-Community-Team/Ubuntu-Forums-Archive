---
title: "tv-card"
date: 2010-04-02
forum: Multimedia Software
---

### Post by speedless on 2010-04-02
Hi
I am new to this forum
I am also new to ubuntu but have manage so far,except for my tv-card.
Seems like Metv and kaffeine cant see the tv-card ?!
I have a asus mycinema-p7131 hybrid,does someone have info on installing this ?
except for this i think ubuntu 10 is great.
Jan

---

### Post by Jose Catre-Vandis on 2010-04-03
I've got one of these - should work out of the box, or has done from Hardy up to Karmic (not tried Lucid yet)

Open a terminal and run the following commands:

```
dmesg > dmesg.txt
```
```
lspci -v > lspci.txt
```

(I have got you outputting the output text files to make life easier for you to post the info back here) This should tell us if the card is recognised and drivers loaded from the kernel.

You should have card=78 tuner=54 foir this tv-card.

There was a signal problem with Karmic but it should be fixed in Lucid

---

