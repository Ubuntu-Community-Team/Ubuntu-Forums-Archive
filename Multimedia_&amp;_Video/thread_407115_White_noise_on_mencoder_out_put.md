---
title: "White noise on mencoder out put"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by apjone on 2007-04-11
When I use mencoder to encode some video files to avi to play on my portable media i get white noise all the way through. here is the code is use

```

#!/bin/bash
mencoder  -noodml $1 -of avi -o $2 -ofps 24 -vf-add scale=224:176 -vf-add expand=224:176:-1:-1:1 -srate 44100 -ovc xvid -xvidencopts bitrate=550:max_bframes=0:quant_type=h263:me_quality=4 -oac lavc -lavcopts acodec=mp2:abitrate=128

```

---

### Post by apjone on 2007-04-12
Is this caused by DRM or the way the files are encoded?

---

