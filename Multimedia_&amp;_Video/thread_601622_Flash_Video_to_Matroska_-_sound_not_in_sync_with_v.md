---
title: "Flash Video to Matroska - sound not in sync with video"
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by siddartha on 2007-11-03
I was getting some clips from youtube and I just get them as .flv files. I have checked the net and usually it is recommended a recoding which is silly as the clips are already of a bad quality. The resulting avi from reconversion is also larger and the picture has lower quality.

So I go and copy the video and audio stream with mencoder
```
mencoder -of avi -ovc copy -oac copy -o video.avi video.flv
```

Than I use the mmg gui to convert from .avi to .mkv

The end result is badly out of sync. Also, it would be nicer to have all done in one step no matter if it's GUI or CLI.

Cheers,
Sidd

---

