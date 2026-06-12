---
title: "Convert MPG to AVI"
date: 2008-01-15
forum: Multimedia Production
---

### Post by vegaj on 2008-01-15
I recently use xDVDShrink to obtain the mpg file of a DVD movie, and I wish to convert the mpg to avi. Does anyone out there know of a program that will accomplish this for me. I would really appreciate your help.

vega

---

### Post by Creative2 on 2008-01-15
:) you could try this

[http://ubuntuforums.org/showthread.php?t=652843](http://ubuntuforums.org/showthread.php?t=652843)
or convertIT
or winff
or terminal
```

mencoder INPUTFILE -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000 -xvidencopts fixed_quant=4 -o OUTPUT.avi
```

---

### Post by vegaj on 2008-01-15
I will give it a try. Thanks

---

### Post by vegaj on 2008-01-15
Worked very well, thanks a lot for your help.

---

### Post by Creative2 on 2008-01-15
what did  you use ?set solved in your topic

---

