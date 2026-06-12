---
title: "[lubuntu] Subtitle Editor"
date: 2020-09-25
forum: Multimedia Software
---

### Post by nekoliko on 2020-09-25
Hi. I just wanted to share what I found on a fresh install of Lubuntu 20.04 to get videos working on SubtitleEditor, after seeing the program complain of not being able to find the decoders for
* H.264 (High Profile)
* MPEG-4.

I notice that in [the most recent thread about this]("https://ubuntuforums.org/showthread.php?t=2391888"), from 2018, still ranking highly in the Google searches I tried, a good answer is lacking. (That thread is now closed.) I found this alone did the trick:

```
[SIZE=4]sudo apt-get install gstreamer1.0-libav[/SIZE]
```

Answers I found elsewhere about installing [FONT=courier new]h264enc[/FONT], [FONT=courier new]gstreamer1.0-plugins-bad[/FONT], or [FONT=courier new]libgstreamer-plugins-bad1.0-0[/FONT][FONT=arial] turned out to be irrelevant in this platform. However, I should note this install of Ubuntu came with VLC already installed.

I hope this will be useful to others.[/FONT]

---

