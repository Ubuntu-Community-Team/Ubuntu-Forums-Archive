---
title: "Convert video into individual frames"
date: 2007-10-01
forum: Multimedia Production
---

### Post by elexhobby on 2007-10-01
Hi..

I am working on a project on video enhancement..

However, I am a newbie to Ubuntu.. Can somebody please let me know how I can decompose a video into its individual frame images, so that I can apply my image processing algorithms to those images..

Thanks in advance.

---

### Post by Mickeysofine1972 on 2007-10-01
Hi

If you get yourself a copy of Lives for ubuntu ([http://www.getdeb.net/release.php?id=1179](http://www.getdeb.net/release.php?id=1179)) it will create a folder full of images for each frame.

Mike

---

### Post by eye208 on 2007-10-02
ffmpeg -i yourvideo.avi frame%06d.png

will convert yourvideo.avi to frame000001.png, frame000002.png, frame000003.png ...

This works for all video and image file types supported by ffmpeg.

---

