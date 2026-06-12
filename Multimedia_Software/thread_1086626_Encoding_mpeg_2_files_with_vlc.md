---
title: "Encoding mpeg 2 files with vlc"
date: 2009-03-04
forum: Multimedia Software
---

### Post by brombo on 2009-03-04
I have installed vlc and ffmpeg from the ubuntu repositorys. I wish to use vlc to encode mpeg 2 video files.  When I try to do this vlc informs me there is no mpeg 2 encoder.  The version of ffmpeg in the ubunutu repository was compiled without including many of the standard video encoders.  I can download ffmpeg from the developers and compile it with all the encoders that are included in the source code.  The question is, is there any way I can make the version of vlc from the ubuntu repository use these new libraries or must I also compile vlc from the souce and put in links to my new libraries with ./configure for vlc?

---

### Post by FakeOutdoorsman on 2009-03-04
If you are using Intrepid, the easiest option is to install the **libavcodec-unstripped-51** package to enable most restricted encoders in FFmpeg.  If you are using Hardy, you can use FFmpeg from the [Medibuntu](http://medibuntu.org/) repository.

---

