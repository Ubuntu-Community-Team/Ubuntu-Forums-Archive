---
title: "Cannot extract a clip from a video using avconv"
date: 2012-11-28
forum: Multimedia Software
---

### Post by rotorcraig on 2012-11-28
I've recently upgraded to Ubuntu 12.10 and am attempting to use avconv (in place of ffmpeg) to extract a clip from a longer video.

The command syntax that I am using is

[COLOR="Gray"]avconv -ss <start-time> -t <duration> -i input-video.mp4 -codec copy output-clip.mp4[/COLOR]

So as I want a 1 minute clip starting 30 seconds into an AVI file

[COLOR="Gray"]avconv -ss 00:00:30 -t 00:01:00 -i input.avi -codec copy out.avi[/COLOR]

What I get is a corrupt output video that appears to be the same length as the original video in the status bar, does starts roughly 30 seconds in, but has audio out of sync with video.

Can anyone see what I'm doing wrong here?

Thanks in advance,

Craig

---

### Post by evilsoup on 2012-11-28
Try putting the output options after the '-i' flag (you should only put options that apply to the input in front of the -i flag). Also, I've never seen this -codec option...
```
avconv -i input-video.mp4 -ss <start-time> -t <duration> -c:a copy -c:v copy output-clip.mp4
```

If that doesn't work, post the output of avconv here in between [code][ /code] tags.

---

### Post by andrew.46 on 2012-11-28
Can you give the command + complete terminal output?

---

