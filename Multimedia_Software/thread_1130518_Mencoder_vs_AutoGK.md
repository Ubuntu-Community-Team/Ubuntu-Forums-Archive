---
title: "Mencoder vs AutoGK"
date: 2009-04-19
forum: Multimedia Software
---

### Post by kfarrell on 2009-04-19
So I have all these TV series episodes I want to convert. In the past I have used AutoGK, each 45 minute episode I shrink to about 300mb with great results.

Now I have dreams of writing a script that I can run in linux using mencoder to get comparable results but I just can't get a good quality rip. 

So if I paste the engine room of my script it will show the options I'm using.

> echo "Converting $FILENAME" >> log.txt
	rm -f frameno.avi
	echo "Audio pass" >> log.txt
	mencoder $FILENAME.vob -ovc frameno -o frameno.avi -oac mp3lame -lameopts vbr=3
	echo "Video pass 1" >> log.txt
	mencoder $FILENAME.vob -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=770:vhq:vpass=1 -oac copy -o $FILENAME.avi
	echo "Video pass 2" >> log.txt
	mencoder $FILENAME.vob -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=770:vhq:vpass=2 -oac copy -o $FILENAME.avi

Well it does the job but it's way fast. Like I can convert a 45 minute episode in about 10-15 minutes (That's all three passes). Compare that to AutoGK which converts it in over an hour.

So mencoder is obviously sacrificing quality for speed. Has anyone got some better options to make mencoder take it's time and do the conversion slowly and with [COLOR="Red"]much[/COLOR] better quality.

Those above options give me a file that's blocky (you can see individual squares all over it) and with a slight interlace. I have used a few of the de-noise filters with not much luck.

Thanks in advance,


Kieran Farrell

---

### Post by andrew.46 on 2009-04-20
Hi kfarrell,

Unfortunately I am not a MEncoder expert but you could try altering your settings to:

```

mencoder input.vob \
        -ovc lavc \
        -lavcopts vcodec=mpeg4:vbitrate=900:mpeg4:mbd=2:trell:v4mv:turbo:vpass=1 \
        -oac copy -o /dev/null && \
mencoder input.vob \
        -ovc lavc \
        -lavcopts vcodec=mpeg4:vbitrate=900:mpeg4:mbd=2:trell:v4mv:vpass=2 \
        -oac mp3lame -lameopts vbr=3 \
        -o output.avi 

```

These are settings I have used successfully before but I will admit to using FFmpeg itself these days. The definitive guide is here:

[http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#menc-feat-dvd-mpeg4](http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#menc-feat-dvd-mpeg4)

This relates to dvds more than TV series but much of the material should still be relevant, but I will admit it is a heavy read :-).

Andrew

---

### Post by FakeOutdoorsman on 2009-04-21
Another option is to use FFmpeg and the libx264 presets.  The presets are fairly easy to use and will give excellent quiality video.  Unfortunately, you have to compile FFmpeg and x264 to take advantage of them. Step-by-step instructions:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by Guitar John on 2009-04-21
I don't have a solution to your problem.  In this department, I am more likely to have questions than answers.  

But I am curious, what is the file size of the files converted rapidly with Mencoder as opposed to those converted more slowly with AutoGK? 

I realize that the file size could be identical and the quality still bad.

---

### Post by swatkins on 2010-11-29
> **kfarrell said:**
> -ovc lavc

The lavc / ffmpeg codec you are using is fast but not best quality.  Try using xvid codec instead, or maybe x264 (this is the best, but very slow).  search the web for mencoder xvid 2 pass or similar.

---

