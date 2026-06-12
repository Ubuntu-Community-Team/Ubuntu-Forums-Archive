---
title: "Mplayer sometimes ignores anamorphic factor while dumping"
date: 2012-08-24
forum: Multimedia Software
---

### Post by free-radical on 2012-08-24
Hello,

while ripping some of my DVDs for usage on NAS, I get into some trouble regarding the aspect ratio of the output, which I don't understand.

There are two DVDs. When simply playing with

```
mplayer dvd://SOMETITLE
```

both have the correct aspect ratio of 1.78:1 and a video stream resolution of 720x576 (and thereby are anamorphic videos?!). The process of dumping the stream to disc with

```
mplayer dvd://SOMETITLE -dumpstream -dumpfile out.vob
```

goes perfectly fine with one of them, producing a dump with the same aspect ratio and resolution as the input. But for the other one, it produces a 1.33:1 output when playing

```
mplayer out.vob
```

Also here, video stream resolution is 720x576, so there is some rescaling, but not with the right factor.

Am I doing something wrong? Or is it a problem with the DVDs? Is there a fuzzy autodetection logic which fails at some time? But, all players, even mplayer itself, can playback them well. If anybody has a solution, a hint or a workaround, please tell me :-)

Touching the actual stream by cropping or scaling is not a nice option. As far as I understood, the problem is with metadata.

Kind regards
Josef

---

