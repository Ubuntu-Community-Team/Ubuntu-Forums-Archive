---
title: "How to intercept audio from a mp3 file?"
date: 2011-01-25
forum: Multimedia Software
---

### Post by NewUserFF on 2011-01-25
Hey,everyone.
Now I have a problem with mencoder.When I tried to use mencoder to interpret a mp3 file (test.mp3) from 1:30 to the end like this :

mencoder -o out.mp3 -oac mp3lame -lameopts cbr:br=128 -of rawaudio -ss 1:30 test.mp3

I found it failed:
ASF file format detected.
[asfheader]audio stream found, -aid 1
Video stream is mandatory!
Exiting......

I'm really not clear where is wrong.Anyone can help?

Sorry,my mother tongue isn't English,so just understand.Thanks;-)

---

### Post by poodoopealeoaph on 2011-01-25
Well, if you are trying to take a video or audio you find on the internet and you want to know how to record it or rip it without losing quality, simply connect your headphone jack on your laptop or desktop to your record or mic jack. Make sure that you aren't clipping or else it will sound like crap though. As long as you aren't clipping, just open a recording program (ie. ardour, audacity) press record, then play the audio. You will have just as good of quality audio recorded right into your audio editing/production suite.

to be sure that you don't lose quality as you compress and export, be sure to export at the highest quality possible in your program. So, if you look under your export settings under "file>export>" look for flac. If you can't find that then shoot for WAV. When asking what quality you want, make sure to select 32bit float.

---

### Post by ron999 on 2011-01-25
> **NewUserFF said:**
> 
ASF file format detected.
[asfheader]audio stream found, -aid 1
[COLOR="Red"]Video stream is mandatory![/COLOR]
Exiting......

I'm really not clear where is wrong.

Hi
mencoder won't accept audio-only files. They must be videos.;)

Try using ffmpeg instead, like this for 90 seconds **hh:mm:ss**:-

```
ffmpeg -i test.mp3 -ss 90 -acodec copy out.mp3
```

---

### Post by vanadium on 2011-01-25
It is utterly unclear what you want to achieve. Converting an mp3 to mp3?

---

### Post by NewUserFF on 2011-01-26
Thanks a million for all your answers.I'll try ffmpeg as ron999 says.
the best.

---

### Post by andrew.46 on 2011-01-26
Hi ron,

> **ron999 said:**
> mencoder won't accept audio-only files. They must be videos.;)

It is just a side-note but if you look in the TOOLS subdirectory of the svn MPlayer source code you will see a small script called *aconvert.sh* which allows MEncoder to deal with audio only files.

---

### Post by hugmenot on 2011-01-27
First of all it’s not an .mp3 file but .asf as it says in the output.

---

