---
title: "Sharing MP3 compression best practices"
date: 2010-08-08
forum: Multimedia Software
---

### Post by Tugdualenligne on 2010-08-08
Hi there,
I just thought I could share the custom settings I have created to encode MP3 using Ubuntu and more particularly using K3b. Just replace the custom command line in K3b with this one to obtain high quality - thus quite fast - MP3 encoding.

lame -r --bitwidth 16 --little-endian -s 44.1 -h --vbr-new -V0 -b96 -B160 -q0 --lowpass 20.5 --tt %t --ta %a --tl %m --ty %y --tc %c --tn %n - %f --id3v2-only

Any comments welcome about other practices or other parameters!

Enjoy 

Tugdualenligne

---

