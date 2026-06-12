---
title: "How do i convert with Mencoder or FFMPEG ???"
date: 2008-05-11
forum: Multimedia Software
---

### Post by Tanjer1588 on 2008-05-11
I have been searching and keep running into the same walls, but how do i use Mencoder or FFMPEG to convert a .avi to a .mp4. I used a few tutorials i ran into but they didnt help or things were left out... like the little details u know. and every thing keeps telling me to intall this and install that and now i have a bunch of stuff i dont need. I just wanna know whats the comand line to convert a video from one type to another ... or is there a manual that i could read that would make some sence? cus the Interfaces i have... like Multimediaconverter and Convertit dont do anything... so im kinda lost... any help would be nice. Thank you

---

### Post by fiddledd on 2008-06-13
I would suggest you use Avidemux, it will convert .avi to .mp4 and more besides. It's a GUI app and has templates for mp4/dvd/mpeg etc. It's easy to use and is (was?) in the repositories. The Home page has docs, but I doubt you'll need them: [http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/)

If it's not in the repositories you can get it from here:
[http://www.getdeb.net/search.php?search_distro_id=7&keywords=avidemux](http://www.getdeb.net/search.php?search_distro_id=7&keywords=avidemux)

---

### Post by FakeOutdoorsman on 2008-06-13
If you're going to use restricted codecs, then MEncoder is easier to setup than ffmpeg in Ubuntu due to ffmpeg not being compiled to support any restricted codecs.  I'm not as familiar with using MEncoder, but these can help:
[HOWTO Mencoder Introduction Guide]("http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide")
[Encoding with MEncoder]("http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html")
[transcoding wiki: MEncoder]("http://videotranscoding.wikispaces.com/mencoder")

As for ffmpeg, you will need to use a third-party repository such as [Medibuntu]("http://medibuntu.org") or [compile ffmpeg yourself]("http://ubuntuforums.org/showthread.php?t=786095") if you plan on using restricted codecs such as mp3 and aac. The basic usage:
```
ffmpeg -i inputvideo.avi output.mp4
```
ffmpeg will use default values for anything you don't specify, such as bitrate.

---

