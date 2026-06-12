---
title: "Video editor"
date: 2013-04-02
forum: Multimedia Software
---

### Post by earthtorob on 2013-04-02
Hey guys.....I've been editing video on my Windows machine for a lot of years.  I use old tools because I have a lot of control.  I'd like to switch over to Ubuntu and video editing is the one thing that is stopping me.  So I have some questions.  I've been looking at video editors and I see 4 main contenders.
Kino
OpenShot
PiTiVi
Cubelerra

They all seem nice but there is a feature that I am looking for and it's daunting to install all of them and use all of them to see if it supports the feature.

I do a lot of interlaced video.  I prefer to split the fields and resize and end up with 60fps video.   I also like to work in the YUV color space.  In windows I use Avsynth and Vdub.  They are old but work well.

Do any of video editors for ubuntu work in that way?  Which is the best for the job in terms of getting clean output?

---

### Post by vanadium on 2013-04-03
Avidemux is quite similar to virtualdub, and serves the same purpose.

As far as I am aware, there is no one stop integrated frame serving solution for linux such as avisynth in Windows. Probably, you can achieve a lot of similar functionality using the command line tools and tricks like named papes etc.

Openshot is a non-linear video editor aimed at the casual user. Cinelerra is more professional but has a steeper learning curve.

---

### Post by earthtorob on 2013-04-04
Oh that looks like it may do it.  Once I have the 60fps "progressive" video I can use the other editors for simple editing.  :)

---

### Post by earthtorob on 2013-04-04
Avidemux doesn't support Dv type-1 or type-2 as input.  So I'll have to  use a highly compressed stream like MPEg or AVI.  This is bad for me I  think.  Well I have a starting point to get started from.  Thanks.  :)

---

### Post by qyot27 on 2013-04-09
> **vanadium said:**
> As far as I am aware, there is no one stop integrated frame serving solution for linux such as avisynth in Windows. Probably, you can achieve a lot of similar functionality using the command line tools and tricks like named papes etc.
Actually, [there is a [partial] solution to that](https://github.com/avxsynth/avxsynth) (the System Setup page is outdated, though).  But I don't think anyone has done the work to get TIVTC (or practically any of the other external plugins) ported over to it.  Alternatively, there is [VapourSynth](http://www.vapoursynth.com/), which does have an [internal ivtc filter](http://code.google.com/p/vapoursynth/source/browse/trunk/src/filters/vivtc/vivtc.c), but has other limitations (no integrated audio support, currently-flaky y4m piping, and while this isn't a limitation, it uses Python so it's not quite the same as writing an AviSynth script).

In terms of broader support, anything that uses FFmpeg (specifically libavformat) can use AvxSynth on Linux and OSX, so long as A) the FFmpeg build is from [after March 20th](http://git.videolan.org/?p=ffmpeg.git;a=commit;h=b9ad009475f3afb76bd2fbd92936dc4d4cd441ec), and B) was built with --enable-avisynth.  And obviously, you also have to have AvxSynth installed.  This means that mplayer2 and mpv can preview scripts directly; I'm not sure of the logistics with mplayer-svn.  x264's CLI interface also has support for it now too.



EDIT: I just realized that the OP is talking about using SeparateFields() and then one of the Resize() filters.  AvxSynth should be able to handle that (the resizing it definitely can; I've not messed with SeparateFields on there but the progress chart on the github wiki lists that one as having been ported).

---

