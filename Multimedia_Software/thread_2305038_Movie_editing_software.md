---
title: "Movie editing software"
date: 2015-12-02
forum: Multimedia Software
---

### Post by Lloydb39 on 2015-12-02
Can anybody give me a tip on good movie editing software for Ubuntu 14.04? I got Win FF but it doesn't work. Says I don't have ffmpeg. Is there another app, or a way to get the missing link? Thanks anyone.

---

### Post by sudodus on 2015-12-02
I'm using ***openshot*** (still in 12.04 LTS, but I think it should work in 14.04 LTS too).

If not, it might also want ffmpeg, and you should install that piece of software. Other people know better how to manage ffmpeg and how get a good up to date and working version ...

---

### Post by FakeOutdoorsman on 2015-12-02
As of Ubuntu 15.04 the real ffmpeg from FFmpeg is available in the repos. Should be good enough for most users.

Ubuntu Trusty users can use [mc4man's PPA](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media).

[FFmpeg development is very active](http://git.videolan.org/?p=ffmpeg.git;a=shortlog;h=HEAD), so if you're doing more than a few encodes, or are serious about it, then use a recent build. Anyone can simply [download a current static build](http://johnvansickle.com/ffmpeg/).

Or if you want the latest & greatest and want to customize you can of course [compile ffmpeg](http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu). Also, if you have a problem with too many ladies pestering you compiling is good birth control.

Depending on the method you use, you may have to tell WinFF where your new ffmpeg is if you want to use that.

---

### Post by Rob Sayer on 2015-12-05
WinFF can use either ffmpeg or avconv.  Did you install an avconv version and not have it set to use that?  Or maybe you used a non repo source and the dependencies aren't sorted out?

However, you won't be too happy with WinFF as a video editor anyway.  It is not an editor.  It just converts formats, and in my experience it doesn't even do that very well.  I use avidemux or handbrake depending on what output format I wantf to convert to.

Avidemux is also a good editor for xvid video.  For h.264 Openshot is good and not that hard to use.

---

### Post by Lloydb39 on 2015-12-05
OK. I dumped WinFF and got Openshot. Everything seems to be fine. Thanks.

---

