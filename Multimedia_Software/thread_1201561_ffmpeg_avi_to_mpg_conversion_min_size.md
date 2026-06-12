---
title: "ffmpeg avi to mpg conversion min size"
date: 2009-07-01
forum: Multimedia Software
---

### Post by nikhilbhardwaj on 2009-07-01
hi
i installed the latest version of ffmpeg and x264
i want to convert my 700mb avi file(s) into 700mb mpg files
so that i can play them in my dvd player

the catch is that the size must remain 700mb(or something less than 1 gb)
so that i can write multiple movies to dvd

i know that there will be loss in quality
and that is perfectly acceptable as long as the movie can be watched without drastic problems

so i want to know how, i can convert those avi files keeping the size to a minimum.

---

### Post by nikhilbhardwaj on 2009-07-06
its been 5 days 
no reply
come on you can do better than that

---

### Post by FakeOutdoorsman on 2009-07-06
Perhaps this simple command will work:
```
ffmpeg -i input.avi -target pal-dvd output.mpg
```

---

### Post by nikhilbhardwaj on 2009-07-11
thanks for replying
but the trouble with that command is that it increases the size of the 700 mb avi to about 3gb
and i want to keep the size to less than 1 gb
a loss of quality is acceptable
hopefully you'll be able to help me with it

---

### Post by FakeOutdoorsman on 2009-07-13
You must come up with a bitrate to reflect the final size you want.  Try some bitrate calculators on the web to help you out.

---

### Post by nikhilbhardwaj on 2009-07-15
[FakeOutdoorsman]("http://ubuntuforums.org/member.php?u=162846") you are the guy who writes those great tutorials
awesome
thanks for thaking the time to help me out

see what i want is mediocre quality 320x240 or something like that looks decent on a 21" tv no widescreen stuff and decent audio quality

so what would the command be to convert the avi to mpg

also you mention these online bitrate calculators
could you please suggest some to me

once again thanks for taking the time to help me.

---

### Post by FakeOutdoorsman on 2009-07-15
I'm glad you liked the tutorials.  I was coming up with a simple command for your video and found a small bug in SVN FFmpeg which I then submitted a patch for, so you indirectly helped improve FFmpeg.  How long is your movie that you want to convert?

---

### Post by nikhilbhardwaj on 2009-07-16
its a documentary 
the death of yugoslavia
six parts nearly 50 minutes each
wanted to convert them and create a dvd with menu

---

