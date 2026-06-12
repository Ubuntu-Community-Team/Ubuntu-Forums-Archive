---
title: "MP4Box join 2 MP4-Files doesn´t work..."
date: 2014-05-17
forum: Multimedia Software
---

### Post by rene10 on 2014-05-17
Hey.

I have 2 MP4-Files.
I try to combine them so:

> -cat 1.mp4 -cat 2.mp4 output.mp4

This gives me a bigger file, but i can´t play it with the mediaplayer.
If i copy the 1.mp4, and name it 2.mp4, and then combine it, it works, but only with the same video.
What ist wrong?
Both are MP4-files..
I hope you can help me :)
Best regards, from Germany, René

---

### Post by Yellow Pasque on 2014-05-17
mp4 is a container and can have different video formats inside.
The first step would be to verify the video/audio codecs:
```
sudo apt-get install mediainfo
mediainfo 1.mp4
mediainfo 2.mp4
```

---

