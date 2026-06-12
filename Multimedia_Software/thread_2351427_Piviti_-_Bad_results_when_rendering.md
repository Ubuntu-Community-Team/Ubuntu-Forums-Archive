---
title: "Piviti - Bad results when rendering"
date: 2017-02-03
forum: Multimedia Software
---

### Post by Fabzil on 2017-02-03
Hi there!

I recently retrieve (very) old videos from 2008 and 2009 that were recorded by a cellphone. I made a small compilation and added music. 
Now I can't get Piviti to render the final video as good as the original files, even though the originals files were not that great!

My originals files are all : 
3GP
192x144
Format: S263
Codec: FFH263
FPS : 250,0   (I guess it's 25 really)
Bitrate: around 130 / 140 kb/s
Audio: 8 KHz
Audio bitrate : 12 kb/s

As you can imagine, my original videos are quite ugly, with massive pixels. Yet, Piviti is managing to render the final video even worse, with massive aliasing and "lines" in the video.

What are the options I should choose to "mimic" the originals file?
I have tried with : 

MP4
192x144
Codec : x264enc
Bitrate : 512 kb/s
FPS : 25

Thank you by advance for your answer

---

### Post by Fabzil on 2017-02-03
Ok, I think I found it out. 
[B]
I was using the "Title" feature[/B], which allows to write on the screen, kinda like a subtitles. 
Because my resolution is so low (192x144) I think the internal processing was creating those horrible lines. But those lines disappear with the "title", which means 99% of the time the video is fine.

I also boosted to 29,97 FPS. It woobles a bit more but it's so much more pleasing to the eye comparing to the 25 FPS.

If this can help anyone...
edit : if anyone knows how to [SOLVED] the topic, please go ahead ;)

---

### Post by Bucky Ball on 2017-02-03
> **Fabzil said:**
> edit : if anyone knows how to [SOLVED] the topic, please go ahead ;)

You get that responsibility. :) Thread Tools> Top right. There is also a link in my signature which explains how to mark as solved. 

Well done fixing.

(PS: Have you tried leaving the original 25fps and upping the bitrate to, say, 2048? Just a suggestion and curious. Also, what is the audio set at? I'm not familiar with the app you're using so not sure how much you can adjust with it. 

Handbrake is another tool you can try for this. Very handy, powerful and flexible. It is in the repositories, i.e. Software Centre or whatever package manager you are using.)

PPS: Yea, just had a look. As I thought; Piviti is a filmaking/editing/production app. You don't want that. You want Handbrake. Built for purpose. ;) You can also do 'batch' render once you have the settings right and do the whole lot while you go off and do something else. Check out [the features here]("https://handbrake.fr/features.php"). Install from Software Centre.

---

