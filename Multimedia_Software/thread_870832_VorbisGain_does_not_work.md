---
title: "VorbisGain does not work?"
date: 2008-07-26
forum: Multimedia Software
---

### Post by Giantics on 2008-07-26
Unfortunately vorbisgain doesn't work on my system (Debian Lenny).

I tried "vorbisgain -g xx file&#8220;.

xx= +20, ogginfo says: 
```
User comments section follows...
        REPLAYGAIN_TRACK_PEAK=1.30494869
        REPLAYGAIN_TRACK_GAIN=-10.32 dB
        REPLAYGAIN_ALBUM_PEAK=1.30494869
        REPLAYGAIN_ALBUM_GAIN=+20.00 dB
```

xx= -20, ogginfo says: 
```
User comments section follows...
        REPLAYGAIN_TRACK_PEAK=1.30494869
        REPLAYGAIN_TRACK_GAIN=-10.32 dB
        REPLAYGAIN_ALBUM_PEAK=1.30494869
        REPLAYGAIN_ALBUM_GAIN=+20.00 dB
```

Seems to be correct? But I can't hear any difference in volume on these two files. I tried Amarok, ogg123 and XMMS2.
Did I missunderstand anything important?

---

