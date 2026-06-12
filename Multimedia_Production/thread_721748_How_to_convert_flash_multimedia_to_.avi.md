---
title: "How to convert flash multimedia to .avi?"
date: 2008-03-11
forum: Multimedia Production
---

### Post by xigen on 2008-03-11
Hey...

How do I convert a flash 9 multimedia to .avi ? (or anything which I can burn on a cd and play in a dvd player).

I recently got married -- and this is the wedding multimedia.

system:  Hardy, AMD64, non-free drivers installed

All the best,

MW

---

### Post by scragar on 2008-03-11
```
ffmpeg -i **file**.flv **file**.avi
```

---

### Post by Creative2 on 2008-03-12
if you have dvd player you can't play avi files....
if you have a dvd-divx player you can play file 

ntsc = america

mencoder INPUT -ofps 30 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000 -vf scale -zoom -xy 720  -xvidencopts fixed_quant=4  -o OUTPUT

pal =europe

mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000 -vf scale -zoom -xy 720  -xvidencopts fixed_quant=4  -o OUTPUT

that what i use ...
if you have many movie clip use fuoco tools you can find on my signature the link..or if you are able you can do a bash script

---

### Post by gsmanners on 2008-03-12
For NTSC you would actually use "-ofps 30000/1001" or your timing would get a little off.

---

### Post by ntlam on 2008-03-21
> **scragar said:**
> ```
ffmpeg -i **file**.flv **file**.avi
```

Thanks for the hint.

---

