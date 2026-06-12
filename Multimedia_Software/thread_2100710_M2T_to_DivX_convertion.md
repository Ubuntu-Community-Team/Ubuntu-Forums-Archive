---
title: "M2T to DivX convertion"
date: 2013-01-02
forum: Multimedia Software
---

### Post by cpeachey on 2013-01-02
My TV plays DivX files.
Kaffeine saves files as M2t
What prog do I need to convert them please?
Chris

---

### Post by evilsoup on 2013-01-02
An M2T is probably an mpeg transport stream, which are commonly used for broadcasting. It may well contain video that your TV can support, which *just* needs to be remuxed to a new container format. You can do this with avconv or ffmpeg from the command-line:

```

avconv -i input.m2t -c copy output.mp4

```You can use 'output.avi' instead if your television doesn't support MP4 video.

If that doesn't work, then you will need to encode to divx.

```

avconv -i input.m2t -c:a copy -c:v mpeg4 -tag:v divx -qscale 6 output.avi

```You may want to change the qscale; 1 gives you best quality, but largest files, and 31 has the worst quality/smallest files. That command will simply copy the audio stream; for maximum compatibility with older systems, you could use MP3 audio (this is generally not the best option for films etc - it doesn't support surround-sound, for example; but it should be supported on everything):

```

avconv -i input.m2t -c:a libmp3lame -q:a 2 -c:v mpeg4 -tag:v divx -qscale 6 output.avi

```

Alternatively, you can look around in Kaffeine's settings to see if it can output the video as something your device can play, in which case you won't have to mess around with this stuff.

---

### Post by cpeachey on 2013-01-02
Thanks for that. I have just tried DeVeDE which converts M2T to AVI which looks to be Ok for the TV.
Thanks for the help.
Chris:guitar:

---

