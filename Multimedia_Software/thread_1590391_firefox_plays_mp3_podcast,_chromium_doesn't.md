---
title: "firefox plays mp3 podcast, chromium doesn't"
date: 2010-10-07
forum: Multimedia Software
---

### Post by Chris1274 on 2010-10-07
I recently installed Chromium and went to listen to one of my favorite podcasts, only to find that it wouldn't play. Like the title says, it plays perfectly well in Firefox. Is there some Chromium extension I need in order to play .mp3 files?

---

### Post by mattwilkes512 on 2010-10-17
Don't know?  I just started using Ubuntu again after a brief dependence on Win7.  I can play mp3 through other browsers but not Chromium.

I want this fixed too.

---

### Post by matthewbpt on 2010-10-17
Type this in the terminal

```
sudo apt-get install chromium-codecs-ffmpeg-extra chromium-codecs-ffmpeg-nonfree
```

Then restart the browser. This will install the patent restricted codecs for use in chromium, including mp3 audio.

@mattwilkes512 Nothing needs fixing you just don't have the right packages installed...

---

### Post by owenll on 2010-10-22
> **matthewbpt said:**
> Type this in the terminal

```
sudo apt-get install chromium-codecs-ffmpeg-extra chromium-codecs-ffmpeg-nonfree
```

Then restart the browser. This will install the patent restricted codecs for use in chromium, including mp3 audio.


Thanks  :)

---

