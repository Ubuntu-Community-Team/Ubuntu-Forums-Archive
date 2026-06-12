---
title: "Transcoding help for FUPPES"
date: 2009-05-29
forum: Multimedia Software
---

### Post by arc2v on 2009-05-29
Well, I've had moderate success with FUPPES this evening.

It has compiled, installed, talks with my XBOX 360, can stream MP3 and JPEG.

So far so good.  The next major hurdle for me to clear is the transcoding.

I have a big collection of FLAC I need to stream to mp3.  The config files look to be in order, but every time I select a FLAC file from the XBOX I get a segmentation fault (core dump) and the server exits.

JPEGS are a bit cleaner.  I tried to set up a resize to my projector's native size (1280 x 720), but whenever I do that I get X's for thumbnails and the images don't load.  When I let them load un-resized, everything works fine, but slow (4MB per picture).

So transcoding isn't working and I can't figure out why.  FLAC, Imagemagick, LAME, and TooLame are all installed.

All help is appreciated.  Thanks.

---

### Post by arc2v on 2009-05-30
Figured it out, I guess, for audio.

I recompiled with --enable-video-transcoding --enable-lame --enable-twolame options.

Apparently you have to do the video transcoding even if you are just transcoding audio.  I guess the drivers/functions don't get compiled in otherwise.

So audio is done now (working).  Now to see about jpg resizing and to *gulp* try video.

Right now this is a test computer.  When I get my actual server box, I may document this step by step -- if for no other reason, than I may have to repeat it someday! :)

---

