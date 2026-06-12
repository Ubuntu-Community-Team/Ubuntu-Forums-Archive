---
title: "Extracting 24vut Audio Streams from DVDs"
date: 2008-12-14
forum: Multimedia Software
---

### Post by ibuclaw on 2008-12-14
[EDIT] Haha... I hate my keyboard :) **s/vut/bit** on the thread title.

Hi,

I have been searching for the longest time about how to extract 24bit audio from DVD .vob files to .wavs without the program outputting an awful hissing noise.

For the better part of my time trying to achieve this, I have been using ffmpeg, but have found that ffmpeg infact **don't support 24bit audio streams**.

So, if this dummy example produces hiss on the output wav:
```
ffmpeg -i [COLOR="Red"]foo[/COLOR].vob [COLOR="Red"]bar[/COLOR].wav
```


Then **the solution is to use mplayer instead.**
```
mplayer -vo dummy [COLOR="Red"]foo[/COLOR].vob -ao pcm:file=[COLOR="Red"]bar[/COLOR].wav
```
What's the difference?
Well, mplayer identifies that the audio stream is 24bit, and [downsamples the .vob input stream to 16bit]("http://osdir.com/ml/video.ffmpeg.user/2005-02/msg00087.html"). So you should be able to convert the output wav to any file you wish now using ffmpeg. :)

Thank you for everyones combined efforts to help other people!
I hope this piece of information proves useful to others.

Regards
Iain

---

