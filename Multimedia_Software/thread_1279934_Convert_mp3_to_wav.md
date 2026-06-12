---
title: "Convert mp3 to wav?"
date: 2009-10-01
forum: Multimedia Software
---

### Post by itzmcgin on 2009-10-01
Is it possible to do this with ffmpeg? [mp3 to wav]

Thanks!

---

### Post by MedianMajik on 2009-10-01
Yessir.  ```
ffmpeg -i file.mp3 file.wav
```
[Google](ubuntuforums.org/showthread.php?t=419781) is your friend :)

---

### Post by hessiess on 2009-10-01
You can using the above command, but there generally isn't any point converting a lossy format into a lossless one.

---

### Post by Bachstelze on 2009-10-01
Probably best to specify the bit depth, signedness end endianness of the PCM stream explicitly:

```
ffmpeg -i foo.mp3 -acodec pcm_s16le bar.wav
```

for 16-bit, signed, little endian PCM (which is the most compatible with other encoders, and is also the ne used on audio CDs).

---

