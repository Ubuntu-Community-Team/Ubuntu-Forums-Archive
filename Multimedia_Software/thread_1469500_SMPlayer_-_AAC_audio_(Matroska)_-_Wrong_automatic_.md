---
title: "SMPlayer - AAC audio (Matroska) - Wrong automatic codec (FFAAC, should pick FAAD)"
date: 2010-05-02
forum: Multimedia Software
---

### Post by aphirst on 2010-05-02
I'm using SMPlayer 0.6.8 (SVN r3213), with MPlayer SVN r31027 (compiled with the vaapi patches). Oh, and I'm using Ubuntu 10.04 (x64_64), and my hardware specs are in my signature.

Some of my video files have AAC audio in them. For some of them, SMPlayer correctly deduces that the correct codec to use is 'faad'. For others, it decides to use 'ffaac'.

For these files, the audio appears to play at half-speed, at a very low pitch. The elapsed time duration follows what the audio 'should' be, with MPlayer closing when the video finishes. Either way, it sounds ridiculous.

It is possible to, after loading a file, tell SMPlayer to use 'faad' for the file, at which point the audio starts working perfectly.

The question is, of course:
Why does SMPlayer/MPlayer pick up the wrong codec in the first place, and is it possible for me to force the usage of the 'correct' codec in such a way that I don't have to do it every time I open a file?

If anyone can point me in the right direction, it'd be much appreciated.

~ Adam

---

### Post by aphirst on 2010-05-02
Aha! After some investigating, the problem seems to lie in the version of MPlayer that's packaged with the VA-API patches. I was using the April mplayer-vaapi release; on using the February release the problems seem to magically disappear.

So, this is an MPlayer regression in SVN. How do I go about contacting the appropriate people?

---

### Post by rvm4000 on 2010-05-02
> **aphirst said:**
> So, this is an MPlayer regression in SVN. How do I go about contacting the appropriate people?

[http://www.mplayerhq.hu/design7/mailing_lists.html](http://www.mplayerhq.hu/design7/mailing_lists.html)

---

