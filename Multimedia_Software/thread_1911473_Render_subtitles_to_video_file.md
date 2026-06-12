---
title: "Render subtitles to video file?"
date: 2012-01-18
forum: Multimedia Software
---

### Post by Pithikos on 2012-01-18
I have an .srt file and a video file .mp4. Now I want to render the srt to the video file.

The reason for this is that I want to upload the video on youtube.

I would like to also be able to choose a background color behind the subtitles as the video already has some subtitles in an other language at some places.

---

### Post by SeijiSensei on 2012-01-19
[http://ubuntuforums.org/showthread.php?t=1910807](http://ubuntuforums.org/showthread.php?t=1910807)

---

### Post by Pithikos on 2012-01-19
> **SeijiSensei said:**
> [http://ubuntuforums.org/showthread.php?t=1910807](http://ubuntuforums.org/showthread.php?t=1910807)

Thanks for the link, though there wasn't much info on how to do it.

Anyway I managed to do it with mencoder:
```
mencoder -sub subs.srt -sub-bg-color 0 -sub-bg-alpha 1 -subfont-text-scale 3.5 -subfont-outline 0 -subfont-blur 0 -subcp iso-8857-9 -ovc x264 -oac pcm -o destination.mp4 source.mp4
```
*-sub subs.srt* tells the encoder which subtitle file to use
*-sub-bg-color 0* tells the encoder to use black as the font-background color
*-sub-bg-alpha 1* tells the encoder to use minimum transparency. 0 will make the font-background totally transparent
*-subfont-text-scale 3.5* sets the subtitle font size to a percentage

All options can be found [here]("http://linux.die.net/man/1/mencoder").

---

### Post by SeijiSensei on 2012-01-19
> **Pithikos said:**
> Thanks for the link, though there wasn't much info on how to do it.

Sometimes I'll answer questions directly, but more often I'll point to some documentation that provides an answer.  Looks like that approach worked for you!

---

