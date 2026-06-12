---
title: "video format conversion"
date: 2012-12-15
forum: Multimedia Software
---

### Post by rdh61 on 2012-12-15
Hi,

I am trying to convert an mp4 video to avi using mencoder and the following code:

```
mencoder <input.mp4> -ovc xvid -oac mp3lame -lameopts cbr:br=192 -xvidencopts pass=1 -o /dev/null
mencoder <input.mp4> -ovc xvid -oac mp3lame -lameopts cbr:br=192 -xvidencopts pass=2:bitrate=-700000 -o <output.avi>
```

found here: [http://ubuntuguide.org/wiki/Video_Conversion#MP4_with_AAC_audio_to_AVI_with_Xvid_.2F_MP3](http://ubuntuguide.org/wiki/Video_Conversion#MP4_with_AAC_audio_to_AVI_with_Xvid_.2F_MP3)

However, I am told:

```
robert@robert-desktop:~$ </home/robert/Videos/TheBigSleep.mp4> -ovc xvid -oac mp3lame -lameopts cbr:br=192 -xvidencopts pass=1 -o /dev/null
No command 'xvid' found, did you mean:
 Command 'xvic' from package 'vice' (multiverse)
xvid: command not found
robert@robert-desktop:~$ mencoder </home/robert/Videos/TheBigSleep.mp4> -ovc xvid -oac mp3lame -lameopts cbr:br=192 -xvidencopts pass=1 -o /dev/null
File not found: 'xvid'
Failed to open xvid.

```

Am I doing something wrong, or is there something wrong with the above commands?

Many thanks.

---

### Post by ron999 on 2012-12-15
> **rdh61 said:**
> Am I doing something wrong...
Hi
This part is wrong:- 
```
</home/robert/Videos/TheBigSleep.mp4>
```
Use [COLOR="Red"]""[/COLOR] quotes instead:-
```
"/home/robert/Videos/TheBigSleep.mp4"
```

And here also:-
```
<output.avi>
```
```
"output.avi"
```

---

### Post by andrew.46 on 2012-12-23
I routinely convert mp4 videos, usually with h.264 and aac, to avi for my wife's TV. But FFmpeg does a better job and I use the following commandline with a recent git FFmpeg:

```

ffmpeg -y -i "input.mp4" -threads auto \
-c:v mpeg4 -q:v 5 -vtag XVID -f avi -mbd rd -flags +mv4+aic -trellis 2 -cmp 2 -subcmp 2 -g 300 \
-c:a libmp3lame -ac 2 -q:a 3 -ar 44100 \
"output.avi"

```

Obviously the input and output filenames need to be changed :). Works nicely on her television and she is happy...

---

### Post by FakeOutdoorsman on 2012-12-23
I believe "-threads auto" is an old alias for "-threads 0", and I think those values may only work for libx264. I'm not sure if mpeg4 can use "-threads", but if it does you would probably have to manually declare a value. I think... I can't test now because I'm away from my computer and my graybeard laptop just retired.

---

### Post by andrew.46 on 2012-12-24
Thanks for that, I will experiment a little...

---

### Post by FakeOutdoorsman on 2012-12-26
I guess I was wrong. That's what happens when I rely on memory. However, I don't get a significant difference between using "-threads auto" and omitting it, and "-threads 1" is significantly slower, so maybe "-threads auto" is default for this encoder too.

I didn't look at the code.

---

### Post by andrew.46 on 2012-12-26
Becomes a little academic for me anway at the moment as I am back on my little dual core laptop having again temporarily shelved the 8 core monster. But good to know with certainty anyway...

---

### Post by rdh61 on 2012-12-28
Thanks ron999. Now the conversion carries through successfully. (Thanks to others too). I'm marking the thread solved now.

---

### Post by andrew.46 on 2012-12-31
Like an old dog I am still worrying away at the *-threads = xx* bone :). I used a 4.5gig dvd dump with mpeg2video and tested mpeg4 conversions using time (explanatory notes for time [here]("http://stackoverflow.com/questions/556405/what-do-real-user-and-sys-mean-in-the-output-of-time1")). This is on my 8 core AMD 8350, FFmpeg achieved 280-290fps with each conversion, although *-threads 4 *dipped to 220fps:

First with *-threads auto*:

```

time ffmpeg -y -i "fist.vob"**[COLOR="Red"] -threads auto[/COLOR]** \
-c:v mpeg4 -q:v 5 -vtag XVID -f avi -mbd rd -flags +mv4+aic -trellis 2 -cmp 2 -subcmp 2 -g 300 \
-an \
"test.avi"

[B][COLOR="Red"]real	8m42.082s
user	39m1.545s
sys	0m19.407s[/COLOR][/B]

```

Then with *-threads 0*:

```

time ffmpeg -y -i "fist.vob" **[COLOR="Red"]-threads 0[/COLOR]** \
-c:v mpeg4 -q:v 5 -vtag XVID -f avi -mbd rd -flags +mv4+aic -trellis 2 -cmp 2 -subcmp 2 -g 300 \
-an \
"test.avi"

[B][COLOR="Red"]real	8m43.592s
user	38m51.965s
sys	0m17.657s[/COLOR][/B]

```

Then with *-threads 8*:

```

time ffmpeg -y -i "fist.vob" **[COLOR="Red"]-threads 8 [/COLOR]**\
-c:v mpeg4 -q:v 5 -vtag XVID -f avi -mbd rd -flags +mv4+aic -trellis 2 -cmp 2 -subcmp 2 -g 300 \
-an \
"test.avi

[B][COLOR="Red"]real	9m13.346s
user	38m21.514s
sys	0m17.100s[/COLOR][/B]

```

Then with *-threads 4*:

```

time ffmpeg -y -i "fist.vob" **[COLOR="Red"]-threads 4[/COLOR]** \
-c:v mpeg4 -q:v 5 -vtag XVID -f avi -mbd rd -flags +mv4+aic -trellis 2 -cmp 2 -subcmp 2 -g 300 \
-an \
"test.avi"

[B][COLOR="Red"]real	11m38.241s
user	35m7.485s
sys	0m15.309s[/COLOR][/B]

```

This is good demonstration of a multi-core cpu at work (user and sys time greatly exceeding real time) and probably also shows that the -threads option does have some influence on encoding time with *-threads auto* being the most efficient. for this conversion, with these codecs and with my computer.... lots of variables there :).

Now to spend some time in the big blue room...

---

