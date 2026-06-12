---
title: "ffmpeg or mencoder. Either will do."
date: 2010-01-08
forum: Multimedia Software
---

### Post by dragos240 on 2010-01-08
Hi. With povray, I created an animated render. Sadly, the 142 frames were saved as individual files. The files are named as so:
animation001.png
animation002.png
animation003.png and so on a so forth until animation142.png. Can I use ffmpeg or something similar like mencoder to merge the images into a video? Possibly 30 fps?

---

### Post by gsmanners on 2010-01-09
I think the docs cover that:

[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-images.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-images.html)

---

### Post by dragos240 on 2010-01-09
> **gsmanners said:**
> I think the docs cover that:

[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-images.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-images.html)

Thanks! :popcorn:

---

### Post by FakeOutdoorsman on 2010-01-09
> **dragos240 said:**
> Hi. With povray, I created an animated render. Sadly, the 142 frames were saved as individual files. The files are named as so:
animation001.png
animation002.png
animation003.png and so on a so forth until animation142.png. Can I use ffmpeg or something similar like mencoder to merge the images into a video? Possibly 30 fps?

Or with FFmpeg:
```
ffmpeg -r 30 -i animation%03d.png -an -vcodec libx264 -vpre hq -crf 22 -threads 0 output.mp4
```

You may need to enable restricted encoders to use *libx264*:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

