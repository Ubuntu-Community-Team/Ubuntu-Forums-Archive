---
title: "What Do We Need W32 codecs for?"
date: 2007-09-05
forum: Multimedia &amp; Video
---

### Post by Rumpty on 2007-09-05
I thought I would get the multimedia side of my Ubuntu installation up to some useful (to me) standard, so installed various gstreamer bits and pieces as required to play my various multimedia files. I have found that the gstreamer codecs? will enable me to play every format I have, using Totem, so started me wondering if the w32 codecs will be needed at all?

---

### Post by chrome307 on 2007-09-05
My understanding of Win32 codecs is that they are codecs that work within a Windows environment eg (if you don't need them don't bother)

Video:

- Win32 VfW DLLs:
    Indeo Video 3.2, 4.1
    Microsoft MPEG-4 v1 & v2 beta
    Microsoft MPEG-4 v3 
    Cinepak Video
    ATI VCR-2
    I263
    Quicktime 6 (includes 3ivX, ZyGo)
    Realplayer 9 (includes RV40)
    xanim (includes 3ivX, Indeo3/4/5)
- Win32 DirectShow filters, decompression-only support:
    Microsoft MPEG-4 v3 ( this decoder is slower than VfW one, 
      but offers wider range of picture control features )
    Windows Media Video 7
    Indeo Video 5.0

Audio:

- Win32 ACM DLLs, decompression-only support:
    Windows Media Audio 
    MS ADPCM
    Intel Music Codec

---

### Post by Rumpty on 2007-09-05
Ok, it seems that gstreamer provides substitutes for a lot of these.

---

