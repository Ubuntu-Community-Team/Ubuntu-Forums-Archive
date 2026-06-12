---
title: "Video Editing &amp;&amp; FFmpeg setup ..."
date: 2008-05-25
forum: Multimedia Software
---

### Post by dbee on 2008-05-25
I want to grab videos from youtube and make a montage. I'm wondering what the best way of doing this is ?

I've already tried most of the packages out there but haven't had much luck. I grab the video in mp4 format, but the only software that'll actually open them is avidemux which only has one channel and so is too basic for my needs. 

In terms of editing software, the open movie editor looks best. However when i try to import the movies, I get an error to the effect of 'Bad frame b reference' or something like that.

I figured i could use ffmpeg to convert mp4 to avi and then just work from there. However ffmpeg just gives me ...

```

ffmpeg -i vid.mp4 -f avi file.avi
....
[mpeg4 @ 0xb7cfc3f0]removing common factors from framerate
Unsupported codec (id=86018) for input stream #0.0

```

I opened up the multimedia repo and installed from there. But i still get the same error :-( It won't convert mp4 to avi.

I've spent way too much time on this already. It should be a fairly simple task. Can anyone point me in the right direction pls ?

Thanks,

---

### Post by Samhain13 on 2008-05-25
For downloading the videos, you can use something like [http://keepvid.com/](http://keepvid.com/) (just saying because I need to complete my train of thought).

I've tried using Open Movie Editor also but I wasn't able to make it work. Avidemux also, not for me. Just yesterday, I had a go with LiVES (available from GetDeb). It seems fine-- at least I can use it. However, until recently, the app I frequently used in editing was Cinelerra. You can get that by following this guide: [http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu](http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu) But if you're using Hardy, it may not be a good idea at the moment. There are also those who say that Blender is a good editor/compositor though I have no personal experience using it as such.

For conversion, you might want to install ffmpeg and/or mencoder from the medibuntu repositories instead of the regular one. You can also try converting the MP4 to AVI with VLC.

---

