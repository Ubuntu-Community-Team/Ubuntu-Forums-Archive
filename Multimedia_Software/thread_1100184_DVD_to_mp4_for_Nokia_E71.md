---
title: "DVD to mp4 for Nokia E71"
date: 2009-03-18
forum: Multimedia Software
---

### Post by stefanadelbert on 2009-03-18
I'm looking for the most efficient way to rip and transcode DVD's to mp4 which are suitable for playback on the Nokia E71.

I have a workable solution atm, but it involves three steps:
[LIST]
[*]rip DVD to VOB files using dvd::rip
[*]transcode VOB files to avi using ffmpeg encode, cropping and shrinking to 320x176
[*]transcoding avi to mp4 using ffmpeg (libx264 for video, libfaac for audio) at the cli (see example command below)
[/LIST]

The command I use to encode to mp4 for the Nokia E71 goes something like this, but it seems to require the input video file to already be at the desired output resolution (320x176 in this case):
```
ffmpeg -y -i inputFILE.avi -acodec aac -ab 72k -s 320×176 -aspect 16:9 -vcodec h264 -b 300k -qcomp 0.6 -qmin 16 -qmax 51 -qdiff 4 -flags +loop -cmp +chroma -subq 7 -refs 6 -g 250 -keyint_min 25 -rc_eq ‘blurCplx^(1-qComp)’ -sc_threshold 40 -me_range 12 -i_qfactor 0.71 -directpred 3 outputFILE.mp4
```

I got this example command from [here]("http://lenrek.wordpress.com/2008/09/26/i-successfully-encode-a-movie-for-e71/").

I would at least like to be able to replace the two transcode steps with one step, i.e. transcode VOB straight to mp4 using libx264 and libfaac at 320x176.

Even better would be to be able to rip straight from DVD to mp4, but maybe the rip to VOB step cannot be avoided.

Has anyone managed this or does anyone have any good tips?

---

### Post by stefanadelbert on 2009-03-18
Seems that [handbrake]("http://handbrake.fr/") has a well established GUI and will implement libx264 (where dvd::rip won't) and it might just do exactly what I'm looking for. I'm looking into it now and will post back if I find a solution. I wonder if it has the ability to use a cluster like dvd::rip...

Stef

---

### Post by inobe on 2009-03-19
handbrake is cool' it's a two click deal

---

### Post by stefanadelbert on 2009-03-19
Handbrake is awesome! Is did exactly what I needed quickly and easily. It's a highly recommended app.

Stef

---

### Post by sbrbot on 2009-08-04
Loot at my blog:

[http://nokia-e71-phone.blogspot.com/](http://nokia-e71-phone.blogspot.com/)

---

### Post by stefanadelbert on 2009-12-10
Thanks for the suggestion, wenling85. But Windows? Yuk.

OK, I take that back. Windows isn't too bad. (ahem)

---

