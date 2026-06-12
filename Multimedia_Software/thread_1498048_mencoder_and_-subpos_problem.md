---
title: "mencoder and -subpos problem"
date: 2010-05-31
forum: Multimedia Software
---

### Post by dschaller on 2010-05-31
I'm trying to hardcode subtitles with mencoder. When I do the following preview, everything looks good:

```
mplayer movie.mpg -sub subs.srt -subpos 90
```

When I then try to re-encode the video with mencoder for DVD format using the same -sub and -subpos flags, the subtitle lines are printed twice, once at the default position 100 and also at the position 90 specified. Specifically, with this command line:

```
mencoder -sub subs.srt -subpos 90 -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=704:480,harddup -srate 48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:aspect=4/3 -ofps 30000/1001 -o moviesubs.mpg movie.mpg
```

I'm using the latest SVN of mplayer/mencoder. What am I doing wrong? Has anyone else had this trouble?

---

### Post by dschaller on 2010-05-31
Well, I think I figured out what was going on. I had a another subtitle file in the same directory with the same filename as the movie. So mencoder was using that subfile as a default (at position 100) and then also adding the position 90 subtitles using the file I had specified. I did a little file renaming and got it to work correctly. Seems like there was a default behavior of mencoder there that I wasn't quite aware of.

---

