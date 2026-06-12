---
title: "Burned a DVD with the wrong audio track"
date: 2013-09-26
forum: Multimedia Software
---

### Post by GrouchyGaijin on 2013-09-26
Hi Folks,

I did something wrong and I hope someone here can tell me how to avoid this mistake in the future.
I have a movie with three audio tracks - Italian, English and German.
The movie is in .avi format.
When I play the .avi file in VLC I can choose which audio track I want to hear.

I attempted to turn this .avi into a DVD to play on my TV.
I succeeded.  The DVD plays just fine.  The problem is that the audio is only in Italian.
I would really like the audio to be in English.
Does someone know what I should do in the future to set the audio track to the correct (or provide a choice from multiple) language on the finished DVD?

Below are the steps I used to make the DVD:

```


1. Convert videos to proper mpeg format


./ffmpeg -i source.avi -aspect 4:3 -target pal-dvd dvd.mpg


2. Add the mpeg to the DVD project using dvdauthor - add multiple files after each file name


dvdauthor -o dvd/ -t dvd.mpg




3. Make .iso file


mkisofs -dvd-video -o dvd.iso dvd/


4. Burn ISO


growisofs -speed=2 -dvd-compat -Z /dev/dvdrw=dvd.iso




```

---

### Post by GrouchyGaijin on 2013-09-27
[COLOR=#ff0000][B]UPDATE

[/B][/COLOR]I found two solutions to my problem but I don't really understand why one works and one does not.

Solution 1:  I did something wrong because this resulted in a file of the audio track with no video.  The audio was however in the correct language.

```


ffmpeg -i source.avi \
    -map 0:0 -map 0:2 \
    -c:v copy \
    -c:a:2 copy \
    output..mpg


```

Solution 2: This seems to have worked perfectly.

```


mencoder -oac copy -ovc copy -aid 2 source.avi -o output.mpg


```

Could someone please explain my error with solution one?
It seems odd that I would need to use mencoder instead of ffmpeg to specify which audio track the output should use.

---

