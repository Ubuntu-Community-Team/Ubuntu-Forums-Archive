---
title: "FFmpeg vs MEncoder; Which do you prefer to use?"
date: 2008-10-18
forum: Multimedia Software
---

### Post by GammaRay256 on 2008-10-18
So which do you prefer to use?  FFmpeg directly, or MEncoder?

I use FFmpeg most of the time, the command line options make more sense to me; I also like FFplay for playing most videos and audio because it is fast and lightweight.
The exception is DVDs, I use MEncoder to encode DVDs (and MPlayer or VLC to play DVDs).

I know FFmpeg is used by MEncoder; but the command line options for using each directly are significantly different and I'm wondering what most people prefer to use.

---

### Post by loell on 2008-10-18
which ever fits the known task, say i googled to convert a certain type of format and it suggest any of the two, i just copy/paste it.

---

### Post by GammaRay256 on 2008-10-19
> **loell said:**
> which ever fits the known task, say i googled to convert a certain type of format and it suggest any of the two, i just copy/paste it.

I agree, and I do the same if I don't know what to enter.  But if I am performing an operation from memory, I can remember FFmpeg better.  Also, when given a choice, I would probably choose FFmpeg over MEncoder.

Example:
ffmpeg -i input.flv -sameq -acodec mp3 -ab 128k out.mpg
*A basic operation for converting a video with a less-supported format to a common format that most programs will support.*

---

### Post by netyire on 2008-10-20
I like mencoder much more then ffmpeg, mostly due to having read more of it's documentation and having used it most of the time. I stumbled across it when looking up the mplayer project; only found out about ffmpeg when mencoder died on a bad flv file :-( Guess familiarity breeds bias :-)

Bias aside though, mencoder and ffmpeg both have their strong points. Mencoder has better video and audio filtering capabilities imho, ffmpeg trumps on file support and error resilience.

PS: Thanks for the nifty ffmpeg command!

---

