---
title: "MOV file error"
date: 2012-05-15
forum: Multimedia Software
---

### Post by nibbslang on 2012-05-15
Hopefully someone can help with this problem.

I have 3 x .MOV files from a HD camera on CD, the first one plays fine in VLC, XINE etc but the other two don't.
when I bring up the properties of the files they have data under the basic tab in the size row but under the Audio/Video tab the video dimensions are 0.
Is this file corrupted?

---

### Post by FakeOutdoorsman on 2012-05-15
If you have access to the original files you can compare the md5sums with the ones on the CD. If they are different they could be corrupted.

```
$ md5sum file.mov /media/cdrom/file.mov
ae1127be297cb3a5574aa9ffdddcbcd0  file.mov
ae1127be297cb3a5574aa9ffdddcbcd0  /media/cdrom/file.mov
```

In this example the two files have the same md5sum, so you can rule out that the files are different although it doesn't not rule out that both are corrupted or damaged.

Also, it would be interesting to see what ffmpeg says about the bad file:
```
ffmpeg -i file.mov
```

---

