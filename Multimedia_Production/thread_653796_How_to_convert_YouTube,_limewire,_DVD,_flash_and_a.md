---
title: "How to convert YouTube, limewire, DVD, flash and any video to iPod touch/classic/nano"
date: 2007-12-31
forum: Multimedia Production
---

### Post by foolsh on 2007-12-31
I like using [rockbox]("http://www.rockbox.org/") then I can just
```
mencoder INPUT_FILE_NAME -of mpeg -oac lavc -lavcopts acodec=mp2:abitrate=96 -af resample=44100:0:0 -ovc lavc -lavcopts vcodec=mpeg2video:vbitrate=300 -vf scale,softskip -ofps 24 -zoom -xy 220 -o OUTPUT_FILE_NAME.mpg
```

---

