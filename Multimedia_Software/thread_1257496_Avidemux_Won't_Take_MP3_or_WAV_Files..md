---
title: "Avidemux Won't Take MP3 or WAV Files."
date: 2009-09-03
forum: Multimedia Software
---

### Post by GroogFish on 2009-09-03
I've got the most recent version of Avidemux but I can't load any of my mp3 / wav files. It just says "Could not open files".

What should I do?

---

### Post by mrgnash on 2009-09-04
```
sudo apt-get install ffmpeg
```

---

### Post by Bucky Ball on 2009-09-04
Try:

sudo apt-get ubuntu-restricted-extras 

... and add the Medibuntu repository to your software sources:

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

The codecs you need do NOT come with Ubuntu. You need to personally agree to download them as they are licensed and third-party. :)

---

