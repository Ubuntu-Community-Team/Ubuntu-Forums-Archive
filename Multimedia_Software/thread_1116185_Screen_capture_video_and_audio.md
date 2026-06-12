---
title: "Screen capture video and audio"
date: 2009-04-04
forum: Multimedia Software
---

### Post by jnbr on 2009-04-04
Maybe this should be in absolute beginners as I'm no expert in linux but this is what I'm trying to do so the question is here (which is another way of saying be gentle and don't give me a hard time if I've asked or done something stupid ;-) )

I am trying to capture the sound and video from a video on the internet, mainly because it's something that I want to go through several times and I don't want to hammer my bandwidth everytime I just want to hit rewind)

So far I have tried this in windows (boo, hiss, yeah I know but it was the first app I found) and it worked but the video was jerky and the sound had to be recorded via the microphone so was low quality.

Now I have tried this in linux (Ubuntu 8.10, linux 2.6.24) using RecordMyDesktop and the video is much smoother, and smaller files and the image is cleaner but the audio fails. If I record the audio in recordMyDesktop then the output ogg file fails to play back, I can step through it to any point in the video but it won't play.

So my next option was to record the audio at the same time using Audacity and then merge, This records the sound but again in low quality (is it using the microphone again?) but I am unable to merge the two streams.

Specifically, and this is where I get to the meat of the question, when I use ogmmerge to combine the video ogg and the audio ogg I either try

ogmmerge -o output.ogg -a part1-audio.ogg -d part1.ogg

which returns "unrecognized character in stream list: 'p'".

or I use

ogmmerge -o output.ogg part1-audio.ogg part1.ogg

which returns "Error: the reader for part1.ogg did not produce a header page". Which seems to imply that RecordMyDesktop does not produce a correct ogg file for video.

Is there any reliable way to get recordmydesktop to record audio (a google suggests this is a problem area so I'm not confident of this)?

Is there any way to get RecordMyDesktop to produce a correct ogg file (assuming this is the problem)

Is there a way to repair an ogg file and add the appropriate headers?

or am I asking the wrong question or going about this the wrong way?

Your frustratedly :-(

---

### Post by rtom on 2009-04-04
I didn't have problems with gtkrecordmydesktop, but there are some other options you may give a try:
[Istanbul]("http://live.gnome.org/Istanbul")
[xvidcap]("http://sourceforge.net/projects/xvidcap/")

---

### Post by jnbr on 2009-04-06
> **rtom said:**
> I didn't have problems with gtkrecordmydesktop, but there are some other options you may give a try:
[Istanbul]("http://live.gnome.org/Istanbul")
[xvidcap]("http://sourceforge.net/projects/xvidcap/")

Ta for that. xvidcap seems a much better option than recordMyDesktop although I still have problems with sound. Now it usualy records the sound (not always which is really confusing) but seems to only record the sound by using the microphone which is really crummy quality, oh well we're slowly getting there. :-)

---

