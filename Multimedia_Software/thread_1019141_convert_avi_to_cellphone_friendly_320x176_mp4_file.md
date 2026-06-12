---
title: "convert avi to cellphone friendly 320x176 mp4 file...ffmpeg to the rescue"
date: 2008-12-22
forum: Multimedia Software
---

### Post by mr_manny on 2008-12-22
found a few ffmpeg posts and after a few unsuccessful attempts, I have found a solution :)

to encode an avi to to an nokia e71 recognized mp4 format:


ffmpeg -y -i inputFILE.avi -acodec aac -ab 72k -s 320x176 -aspect 16:9 -vcodec h264 -b 300k -qcomp 0.6 -qmin 16 -qmax 51 -qdiff 4 -flags +loop -cmp +chroma -subq 7 -refs 6 -g 250 -keyint_min 25  \
-rc_eq 'blurCplx^(1-qComp)' -sc_threshold 40 -me_range 12 -i_qfactor 0.71 -directpred 3 outputFILE.mp4


original file was 700MB, resulting mp4 encoded file slightly less then half @300MB...quality is excellent :)

even though I don't foresee watching many video's on this amazing phone, I thought I would share my findings...

hh,
manny

---

### Post by djhvt on 2008-12-31
Hey Manny...or anyone famliar with this approach,

So i have an E62 and want to do exactly what this post says, but i have no clue what this post is telling me to do nor do i have any idea what ffmpeg is lol. 

can someone dumb this down a bit and walk me through the actual steps? My delicate psyche will thank you when im on my 13 hour bus odyssey and the only electronic device (with a battery worth a damn) i will have is my cellphone

happy new year!

---

### Post by ruddha on 2009-01-01
I use handbrake to encode mp4's for my psp. Works like a charm:
[http://handbrake.fr/](http://handbrake.fr/)

They have a ubuntu *.deb.

---

### Post by andrew.46 on 2009-01-01
Hi djhvt,

> **djhvt said:**
> So i have an E62 and want to do exactly what this post says, but i have no clue what this post is telling me to do nor do i have any idea what ffmpeg is lol. 

ffmpeg is the greatest converter in Linux. Some would see it as a little difficult but when someone has done the hard yards and produced the syntax for you it is dead easy :-).

> can someone dumb this down a bit and walk me through the actual steps? My delicate psyche will thank you when im on my 13 hour bus odyssey and the only electronic device (with a battery worth a damn) i will have is my cellphone

It is my personal opinion that you would be best to compile your copy of ffmpeg from source but never fear there is a great guide on the forums:

HOWTO: Compile the latest ffmpeg and x264 from source
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

And then use the syntax suggested by our friend:

```
ffmpeg -y -i [COLOR="Red"]**inputFILE.avi**[/COLOR] [COLOR="RoyalBlue"]**-acodec aac**[/COLOR] -ab 72k -s 320x176 -aspect 16:9 **[COLOR="RoyalBlue"]-vcodec h264[/COLOR]** \
-b 300k -qcomp 0.6 -qmin 16 -qmax 51 -qdiff 4 -flags +loop -cmp +chroma -subq 7 \
-refs 6 -g 250 -keyint_min 25 -rc_eq 'blurCplx^(1-qComp)' -sc_threshold 40 \
-me_range 12 -i_qfactor 0.71 -directpred 3 **[COLOR="Red"]outputFILE.mp4[/COLOR]**
```

I have obligingly made the input file and the output file red for you, and the audio codec (aac) and video codec (h264) blue. The rest is clever manipulation of small parameters: if it looks good on his phone it will look good on your identical phone :-).

All the best,

  Andrew

---

### Post by djhvt on 2009-01-03
Andrew, thanks so much! You rock.

---

