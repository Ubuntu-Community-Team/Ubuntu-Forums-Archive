---
title: "mp3 codec // compression"
date: 2010-04-02
forum: Multimedia Software
---

### Post by tehtrb on 2010-04-02
hi

i'm not sure if i'm posting this in the right category, but due to an incomplete torrent i'm missing exactly 16384 bytes of an 33.4mb mp3 file, encoded at 128kbps/44khz, and i'd like to know how much playtime that is

# here appropriate formulation, similar to "does anyone have any info"

ty4 yr time
tehtrb

---

### Post by Chronon on 2010-04-02
If it's CBR then you can just use the bitrate to figure out how much time those bits correspond to

16834 b (1s / (128*1000b)) = 0.128 s.

If it's VBR then it's more difficult to say.  Is the file playable?  There should be length information in the metadata header.  You could take the difference of the actual file length and the reported length if the file is playable.

---

