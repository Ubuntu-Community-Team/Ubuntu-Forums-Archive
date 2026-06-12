---
title: "mkv to xvid avi conversion"
date: 2010-06-07
forum: Multimedia Software
---

### Post by Link742 on 2010-06-07
hey does anyone know how i can convert mkv files to avi's that will work on my ps3.

---

### Post by Jose Catre-Vandis on 2010-06-07
This little script certainly does the conversion, but not sure about the ps3 compatibility:
```
#!/bin/sh 

INPUT=$1 
OUTPUT=$2 

mencoder $INPUT \
-ss 00:10:00 \
-oac pcm \
-ovc xvid -xvidencopts fixed_quant=4 -of avi \
-o "$OUTPUT"
```

You might want to re-encode the audio again to reduce file size (mencoder can't yet handle ac3)

---

