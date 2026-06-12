---
title: "Too many audio packets in the buffer"
date: 2010-10-12
forum: Multimedia Software
---

### Post by xMbx on 2010-10-12
Hello,

i got major problems with mencoder.

I work like this.

1.) Demux Audio.
2.) 2 Passes Encode. The second Encode includes the Audio.

And there i got the problem:

Too many audio packets in the buffer: (4100 in 1043395 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

I tried likely anything possible.

How to fix that ?

Before that i got the issue with demuxing the audio where i got a massive amount of "Too many buffered pts" errors. I overcame this by adding the nocorrect-pts option.

---

### Post by rayray519 on 2011-03-22
Where do you add the " nocorrect-pts" option exactly?
Thanks,

---

