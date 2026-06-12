---
title: "ffmpeg2theroa output never has audio"
date: 2009-07-05
forum: Multimedia Software
---

### Post by derekeverett on 2009-07-05
For a couple days now I have been trying to convert video using ffmpeg2theora. My output never has audio. I am about at my wits end with it.

I have tried to convert .mpg and .avi files. Never any audio in the output. I have googled this and gone over the man pages. Every tutorial I have watched - even a few video tutorials - it just works for them.

Is there something I may be missing? 

Only when I work with audio/video do I miss the mac !

---

### Post by andrew.46 on 2009-07-05
Hi derekeverett,

> **derekeverett said:**
> For a couple days now I have been trying to convert video using ffmpeg2theora. My output never has audio. I am about at my wits end with it.

You could very well be limited in your ability to transcode audio by your version of FFmpeg, which ffmpeg2theora uses for this process. Have a look at the Fakeoutdoorsman's page:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg 
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and follow the directions for your version of Ubuntu. I would expect that after you have done this ffmpeg2theora *should* roar to life :-).

All the best,

Andrew

---

### Post by derekeverett on 2009-07-05
Thanks for that. I am looking through it now.

I guess I should have mentioned. I simply want to convert to .ogg

But this info is helpful too for other times so thanks again.

---

### Post by andrew.46 on 2009-07-05
Hi derekeverett,

> **derekeverett said:**
> I guess I should have mentioned. I simply want to convert to .ogg

But I suspect that the problem has to do less with the *output* of ffmpeg2theora and more with the audio type of the *input* file. If your installed copy of FFmpeg cannot read or transcode the audio of the input file I suspect that ffmpeg2theora will create an output file with no sound, which matches your situation pretty closely :-).

Andrew

---

### Post by derekeverett on 2009-07-05
I, derekeverett officially owe andrew.46 one beer!!!

Thanks man works like a charm now!!!

---

### Post by andrew.46 on 2009-07-05
Hi derekeverett,

> **derekeverett said:**
> I, derekeverett officially owe andrew.46 one beer!!!

I raise my glass in thanks :-).

Andrew

---

