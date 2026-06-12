---
title: "software to export all frames of a video"
date: 2009-08-17
forum: Multimedia Software
---

### Post by pythonscript on 2009-08-17
Is there a software package in the repository that will let me export every frame of a video as a separate image, say, to a directory of my choosing? I know this is an incredible amount of pictures, but I have a use for it, so if anyone knows of one, that'd be great. Preferably something command line with a nice, simple command. :)

```
export my_video.avi
```

---

### Post by Shapierian on 2009-08-17
ffmpeg -i in.avi out%05d.png

---

### Post by pythonscript on 2009-09-05
That works great. Thank you!

---

