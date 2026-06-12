---
title: "Checksum &amp; high quality in lame @ Sound Juicer"
date: 2007-10-29
forum: Multimedia Production
---

### Post by vbtricks on 2007-10-29
Salut,

I already found out how to produce MP3s with constant bitrate using Sound Juicer:

```

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=1 vbr=0 bitrate=160 ! id3v2mux

```

But unfortunately I did not find out, how to include checksums and use quality level 0 (means very high).

Anybody already had that issue, solved it and can help me?


Thanks in advance,

Stefan

---

