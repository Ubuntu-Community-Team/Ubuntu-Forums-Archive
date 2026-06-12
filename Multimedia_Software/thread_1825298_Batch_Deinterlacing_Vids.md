---
title: "Batch Deinterlacing Vids"
date: 2011-08-15
forum: Multimedia Software
---

### Post by creiss on 2011-08-15
Hello all!

I just came back from my vacation (yay) and on that I took a camcorder along. All good, but the vids the cam recorded are all interlaced (yuck) and for my purposes I need them not to be. We are talking about roughly a hundred vids here.

So a video conversion tool that is (nearly) losless, does deinterlacing and converts from .mod to .avi would be awesome.

Anyone can point me into the right direction here?

Thanks,
Christian.

---

### Post by fdrake on 2011-08-15
try:
```
ffmpeg -i yourfile.mod -vcodec rawvideo -acodec pcm_s16le -r 15 -s 720x480 -aspect 4:3 yourfile.avi
```

---

### Post by creiss on 2011-08-20
That didnt help.

What did help was

```

ffmpeg -iwmv3 -acodec pcm_s16le -deinterlace -aspect 16;9 ~/Desktop/converted/`basename $i .MOD`.avi

```

Now its deinterlaced. The Input file is 4:3, tho, I need it to scale / resize / fit to 16:9 (the video is 16:9, looks squeezed).

Any ideas on that? :D

-Chris

---

