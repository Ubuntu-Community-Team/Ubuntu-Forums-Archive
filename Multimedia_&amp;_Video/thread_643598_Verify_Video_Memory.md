---
title: "Verify Video Memory"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by tedk89 on 2007-12-17
Ok so I am pretty new just got my laptop set up..realize your talking to a newb :) 

Here goes 
I have nvidia 8600m gt. I want to find out the exact on board video memory it has.Previously vista said it was 256mb, now 7.10 gutsy with the nvidia driver fron envy says I have 512mb. How much vram do I really have? also I am running 64bit.

---

### Post by eth on 2007-12-18
type in a terminal

```
lspci -v
```

and search for your videocard in the output...if it's too much mess just

```
lspci -v > mypci.txt
```

and open the file mypci.txt in your favourite text editor, the search for "VGA" and there you go

---

### Post by tedk89 on 2007-12-19
thanks got it its really a 256mb card.

---

