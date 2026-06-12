---
title: "ytfzf playback too slow"
date: 2022-07-12
forum: Multimedia Software
---

### Post by o-pos2 on 2022-07-12
Hello, I have Ubuntu 20.04.2 LTS. I am trying to play Youtube videos via the command line using the ```
ytfzf -t
```. Everything works well except for the speed, which is very slow. I'm not looking at 4K or 60fpm videos, nothing fancy. Just regular HD videos like 720 or 1080 quality. MPV works well and the online connection is good - meaning, if I try to play the same video on the youtube website, it will work fine.

I did do quite a bit of the online search, and tried different recs - most recently ended up creating a file mpv.conf under.config/mpv, and entered the code ```
ytdl-format=bestvideo[height<=?720][fps<=?30][vcodec!=?vp9]+bestaudio/best
```

Nothing seems to be helping.

Any help would be appreciated.

---

### Post by QIII on 2022-07-12
As ytfzf can be used to circumvent YouTube's ToS to download YouTube content, this discussion is disallowed.

Please refer to [this]("https://ubuntuforums.org/showthread.php?t=2439118").

Closed

---

