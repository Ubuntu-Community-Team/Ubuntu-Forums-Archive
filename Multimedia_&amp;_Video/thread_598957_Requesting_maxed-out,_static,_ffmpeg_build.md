---
title: "Requesting maxed-out, static, ffmpeg build"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by mukiex on 2007-10-31
I'm at wit's end here trying to make a build of FFMPEG that can spit out an iPod or Xbox 360 compatible MP4 file.

I installed Thinliquidfilm and Vive, and they both hit a brick wall at that exact same point : FFmpeg can't encode AAC.

I've tried FFMPEG from Medibuntu, and no such luck.

Now, let me explain :

A source version of ffmpeg I can ./configure, make, etc., and a list of the proper flags to set up, would be fine. I've heard newer SVN builds don't work quite right so I've been wary of trying that, and even if I wanted to, I don't know which conglomoration of flags to set up to make sure everything ffmpeg is capable of gets compiled in.

Also, setting -acodec to : AAC, LIBFLAAC, or even just FLAAC is a no-go, even with the medibuntu upgrade. I still get the same error :
Unknown codec 'AAC' (or 'LIBFLAAC', etc.)

Any help would be greatly appreciated, and a simple static binary ffmpeg executable would be fantastic. Using Ubuntu Gutsy w/ medibuntu repo. (I think that's the only non-standard repo I added)

---

### Post by mukiex on 2007-11-02
No such luck? =(

---

### Post by victor.zamanian on 2007-12-13
> **mukiex said:**
> I'm at wit's end here trying to make a build of FFMPEG that can spit out an iPod or Xbox 360 compatible MP4 file.
...
I've tried FFMPEG from Medibuntu, and no such luck.
...
Also, setting -acodec to : AAC, LIBFLAAC, or even just FLAAC is a no-go, even with the medibuntu upgrade. I still get the same error :
Unknown codec 'AAC' (or 'LIBFLAAC', etc.)
...
Using Ubuntu Gutsy w/ medibuntu repo. (I think that's the only non-standard repo I added)

This might be a stupid question but did you actually put "AAC" and "LIBFLAAC"? I haven't really tried entering the codec names in upper-case, but in my experience it should be either "faac" or "libfaac," in lower-case. Try them both and see what happens -- I believe that works for me using the Medibuntu-repository version.

Otherwise you could maybe look on-line for builds of ffmpeg that include most of the codecs you need. I found a repository; it's not up-to-the-minute with the official subversion trunk of ffmpeg, but it does well on my machine.

BIG NOTE: These builds are Windows binaries, so use the 'wine' software to run them (something I also haven't tried yet):
```
sudo aptitude install wine
``` to install. I actually just boot into Windows to use the binaries with a GUI front-end called 'ffe,' because I need to use iTunes anyway to transfer the encoded videos to my iPod nano. (No, the gtkpod and those other programs didn't work for me with the new 3rd-gen nanos :-/)

Good luck to you!

---

