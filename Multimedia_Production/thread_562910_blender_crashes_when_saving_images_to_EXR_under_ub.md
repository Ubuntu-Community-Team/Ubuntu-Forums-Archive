---
title: "blender crashes when saving images to EXR under ubuntu"
date: 2007-09-29
forum: Multimedia Production
---

### Post by mallow on 2007-09-29
I`m having a problem with the current release of blender. I`ve posted this to Blender forums, but I think that this could be ubuntu related (maybe dependencies issue?) as it`s all OK under Windows or Debian linux.

Blender 2.45 crashes every single time when saving to EXR. It was all OK with 2.44. When I open any file (including default scene), render to EXR and try to save Blender crashes. Blender console gives me only:
"Segmentation fault (core dumped)"
I work on ubuntu linux 7.04. Tested this on laptop with Intel Core Duo processor on board. I also tried to Anim frame 1 and it`s the same result. Blender renders the picture, but when it`s trying to save it it crashes. 
Blender also crashes when I try to open EXR file with blender`s composite editor (you know, with Add->Input->Image).
When I select an EXR image and hit Enter blender crashes. And again, it`s all OK with 2.44 release.

Another thing I`ve noticed: in fact 2.45 saves the EXR file, but not exacly. What I mean is that it probably crashes during saving and that explains one thing: EXR output image from 2.44 is 265,8 KB and EXR image from 2.45 (the same
scene!) is 157,9 KB.

This thing really bothers me as I can`t use EXR format with 2.45 and as you may all know it`s really helpful when Compositing :-(

---

