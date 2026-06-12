---
title: "x264 Avidemux audio sync issues"
date: 2007-10-04
forum: Multimedia Production
---

### Post by ashughes on 2007-10-04
I am having an issue encoding to x264.  I use dvd::rip to get the vobs on my computer and then x264 to encode.  I have tried lame and ac3 but both of them do not sync properly with the video.  There is a delay.  The lag seems to be much worse on ac3.

I have been encoding with xvid4 and it works ok, however the quality is so bad compared to x264.

I am using the default settings for x264, perhaps there is something I have to do to get the audio synced properly.

Has anyone run into this and care to share their info?

---

### Post by ashughes on 2007-10-04
> I use dvd::rip to get the vobs on my computer and then x264 to encode.

This should read:
> I use dvd::rip to get the vobs on my computer and then avidemux using the x264 codec to encode to avi.

---

### Post by BLTicklemonster on 2007-10-21
I'm having the same problems with a dvd I ripped, too. I wonder if anyone knows a fix for this? There's some stuff I want to copy from the movie and save, but everything is out of whack.

---

### Post by robertlankford on 2008-01-31
FWIW, I have the same problem.  I'll rip something with DVDFab HD Decrypter (wine) and use AVIDemux to churn it into x264 with a lame audio track.  Almost without fail, the audio is out of sync.  So, I invariably have to open the avi I just created and copy the video/audio tracks with a shifted audio value (that takes me a couple of minutes to figure out) in order to fix the video.

Anyone have any information on this?  Love the AVIDemux app., by the way.  Great job!

---

### Post by eye208 on 2008-02-01
By default, x264 in Avidemux generates B-frames. AVI has no support for B-frames. Xvid supports B-frames in AVI using a technique called "packed bitstream", but it's basically a hack and not part of the MPEG-4 specification.

AVI has several other shortcomings that may affect A/V sync. For example there is no support for VBR audio or VFR (variable frame rate) video.

Use MP4 instead.

---

### Post by jocheem67 on 2008-02-01
yeah, true.

The way to go is using AAC ( faac ) for encoding audio, using x264 for video, and putting it together with the mp4 container...
I'm sure the A/V syncing will be okay.

---

### Post by theacoustician on 2008-02-01
> **jocheem67 said:**
> yeah, true.

The way to go is using AAC ( faac ) for encoding audio, using x264 for video, and putting it together with the mp4 container...
I'm sure the A/V syncing will be okay.

I might offer that you'd want to use Nero's reference AAC encoder instead of faac, since I have yet to find a way to encode multichannel AAC with faac.  Nero can do it and they now have a Linux native version of their codec free for download.

As for containers, ditch AVI already.  Its an ancient format of little use anymore.  Use Matroska, MP4, or even MOV and I think you'll find better results.

---

### Post by rootkit on 2008-02-01
try with harddup as last filter, if you are using mencoder.

I do it with my tools: [http://ubuntuforums.org/showthread.php?t=684571](http://ubuntuforums.org/showthread.php?t=684571)
encode the same sample and look if they are in sync.

Bye

---

### Post by jocheem67 on 2008-02-02
Of course there's still the issue that standalones won't play mp4.

It's coming round slowly though...

I hope that x264 will be the codec for the future and t won't be like mp3, namely that sticky:)

What about using x264 in an ogm container??
Ayone using that??

---

### Post by eye208 on 2008-02-02
> **jocheem67 said:**
> Of course there's still the issue that standalones won't play mp4.
If they can't play MP4, they usually can't play H.264 in AVI either, only Xvid/DivX.

> I hope that x264 will be the codec for the future and t won't be like mp3, namely that sticky:)
I hope some day FAAC will surpass LAME in terms of quality. Right now this is not the case. At low bitrates, LAME sounds better than FAAC. Although MP3 audio in MP4 containers is consistent with the MPEG-4 specification, Quicktime and Flash can't handle it, so you have to use AAC for compatibility.

> What about using x264 in an ogm container??
Ayone using that??
Some time ago, OGM was very popular in the anime fansub scene, but later it was replaced by Matroska. Today OGM is pretty much dead. If you want to mux MPEG-4 video with Vorbis audio or SRT/SSA subtitles, Matroska is the way to go.

---

