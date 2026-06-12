---
title: "avconv"
date: 2012-06-11
forum: Multimedia Software
---

### Post by baxy77bax on 2012-06-11
Hi, 


can anybody give me an example on how to convert *.MPG  to *.avi without loosing quality. Reason i'm asking is because the avconv has ridiculously long documentation that is of no use to me  since i'm not a pro or anything....


Thank you 


baxy

---

### Post by evilsoup on 2012-06-11
AVI supports the mpeg video codec, so you can completely losslessly copy the streams.

avconv -i input.mpg -acodec copy -vcodec copy output.avi

should do the trick, and in only slightly more time than a cp function.

---

