---
title: "music visualization -&gt; movie file"
date: 2011-12-02
forum: Multimedia Software
---

### Post by i.r.id10t on 2011-12-02
I'm trying to record the visualizations created by ffplay, vlc, etc. for an mp3 file into a movie.

I found [http://ubuntuforums.org/showthread.php?t=1497453](http://ubuntuforums.org/showthread.php?t=1497453) - but the links to glc are all dead - server isn't around, and archive.org has some content but not the build script or source files :(

I've tried vlc, but the visualizations aren't a standard output stream it can re-direct.

I've tried ffplay, but it only plays.  And ffmpeg can't play the file/generate the visualizations, only do the transcoding.

Help?

---

### Post by i.r.id10t on 2011-12-02
OK, found a non-Free windows program to do this... 

But I still want to do this Free!  I've got Free music to go with it, so ...

---

### Post by MG&amp;TL on 2011-12-02
Completely agree.
 

EDIT: never mind, glc's dead. :(

---

### Post by i.r.id10t on 2011-12-05
*bump*

---

### Post by Cs0hu on 2012-07-29
mhm, this question seems to be six months old so it seems there's little hope. I can't imagine it's not possible. Linux is all about streaming everything to everywhere. I'd like to be able to get the output of vlc or movie player's visualization together with the mp3 its playing into a video file as well.
All i find is people suggesting a desktop recorder but that doesnt really cut it imo. I found one other entry on a blog, a pipeline longer than the transsiberian using gstreamer to mix audio and visualization output but i get so many obscure errors i'm a bit discouraged. Someone somewhere has to know something about it. I looked for plugins in vlc that do this but they seem non-existent as well. Call me lazy but i don't feel like capturing little bits and then knitting them together in a video editor just to try something out. If anyone could help i'd be most grateful

---

### Post by FakeOutdoorsman on 2012-07-30
Here's a method using ffmpeg with the *showwaves* filter. I don't use the version from the repository, so I'm unsure if it contains this filter. If not then you can compile ffmpeg: [How To Compile FFmpeg and x264 on Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide).

Example command:
```
ffmpeg -f lavfi -i amovie=audio.ogg,asplit[out0],showwaves[out1] -q:v 2 -b:a 192k out.mpg
```

---

