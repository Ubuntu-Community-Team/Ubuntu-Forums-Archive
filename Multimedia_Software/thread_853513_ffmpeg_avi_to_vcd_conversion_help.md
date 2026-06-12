---
title: "ffmpeg avi to vcd conversion help"
date: 2008-07-08
forum: Multimedia Software
---

### Post by Zulu-Zeffir on 2008-07-08
I've hunted around and would like to know if anyone has a solution.  I am trying to convert an avi to vcd with the following command syntax.  The process works, but the final result has no sound.  Any ideas?  I must be missing something.

```
ffmpeg -i movie.avi -y -f vcd -vcodec mpeg1video -map 0.0:0.0 -b 1150 -s 352x240 -r 29.97 -g 12 -qmin 3 -qmax 13 -acodec mp2 -ab 224 -ar 44100 -ac 2 -map 0.1:0.1 movie.mpg

```

---

### Post by Zulu-Zeffir on 2008-07-10
Well, I didn't figure it out but ended up using DeVeDe instead.  I'm still interested in a solution if anyone can see a syntactical error on my part.  Thanks.

---

### Post by FakeOutdoorsman on 2008-07-10
FFmpeg comes with some preset targets including vcd.  The others are: "svcd", "dvd", "dv", "dv50", "ipod".  You can add the pal- or ntsc- prefix to each target to apply a frame rate if you need to.  The ipod target is currently only avilable if you compile the latest FFmpeg since the version from the repository is outdated.  Try this command:
```
ffmpeg -i movie.avi -target vcd movie.mpg
```
**Update:** Your command was trying to encode in bits/s instead of kb/s.  Add a "k" after each bitrate:
```
ffmpeg -i movie.avi -y -f vcd -vcodec mpeg1video -map 0.0:0.0 -b 1150k -s 352x240 -r 29.97 -g 12 -qmin 3 -qmax 13 -acodec mp2 -ab 224k -ar 44100 -ac 2 -map 0.1:0.1 movie.mpg
```
You could probably also remove the "-map" options.

---

