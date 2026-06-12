---
title: "Convert .wav to .raw"
date: 2007-04-15
forum: Multimedia &amp; Video
---

### Post by hellmet on 2007-04-15
Gyachi plays sounds that are in .raw format. I'd like to customize those sounds, but I've no clue how I could convert my audio files into  .raw .. 
Any help on this would be grateful .. Thanks

---

### Post by tbroderick on 2007-04-15
To convert from .wav to .raw, use sox. Open a termianl and use;
```
sox -V -r 44100 -w -c 2 -s audio1.raw audio1.wav
```

If converting from ogg use oggdec;
```
oggdec -R audio.ogg
```

---

### Post by hellmet on 2007-04-15
well, it works.. but the files don't render fine at all.. anyother way to convert?? also, what do I use to play these .raw files?

---

