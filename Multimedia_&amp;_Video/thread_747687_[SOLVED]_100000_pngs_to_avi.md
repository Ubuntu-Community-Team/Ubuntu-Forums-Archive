---
title: "[SOLVED] 100000 pngs to avi?"
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by ipburbank on 2008-04-06
I use blender 3D, and for a render farm I use BURP. but when I get the PNGs back I have to make them an avi video myself. so another title could be stop motion, but when i searched for that i got people saying that i should use stop motion. Stop motion quits while trying to import the files about 10% way through. What is the command to do this in the terminal? I assume it uses ffmpeg, but my guessing got me nowhere.

Any help would be useful,
thanks in advance,
Istvan

---

### Post by olejorgen on 2008-04-06
From mencoder's man page:
> 
       # Decode/encode multiple files from PNG,
       # start with mf://filemask
       mf=type=png:fps=25

So I guess something like this:
```

mencoder "mf://*png" -mf type=png -o out.avi -ovc xvid -xvidencopts pass=1
# or
mencoder "mf://*png" -mf type=png -o out.avi -ovc raw

```

---

