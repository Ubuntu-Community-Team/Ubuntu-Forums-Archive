---
title: "mencoder: best setting for encoding a bunch of png files"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by Timtro on 2007-05-10
Hi All,

Several years ago, I wrote a program that creates an ordered set of png files. I've been using mencoder to encode the pictures into an .avi file. I've used the following methods:

Two pass (not so good):```

mencoder mf://*.png -mf w=720:h=400:fps=25:type=png -ovc raw -oac copy -o output.avi

mencoder -o /dev/null -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1500:vhq:turbo:vpass=1 output.avi

mencoder -o output_file.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1500:vhq:vpass=2 output.avi

```

Single pass with DivX (a little better)
```

mencoder "mf://*.png" -fps 24 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1400 -ffourcc DIVX -vf scale=640:360 -o aSi_meltcool.avi

```


I'm still not overly happy with the results. There are still a LOT of artefacts. The animations are of coloured balls (atoms) against a white background. These balls tend to leave an 'essence' behind them, and details are lost after the first frame.

Can anyone give me a better solution?

Thanks!

---

### Post by Timtro on 2007-05-12
* bump *

---

