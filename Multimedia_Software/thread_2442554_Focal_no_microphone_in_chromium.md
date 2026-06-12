---
title: "Focal: no microphone in chromium"
date: 2020-05-04
forum: Multimedia Software
---

### Post by abovett2 on 2020-05-04
I can't get my microphone to work in Chromium under Xubuntu 20.04 Focal. I had a similar problem under Xubuntu 19.10 Eoan but was able to fix it by adding the audio-record permission to the chromium snap via:

```
snap connect chromium:audio-record :audio-record
```

However, this doesn't solve the problem under Focal. I see that there is an additional pulse-audio "plug" listed when I run "snap connections" which wasn't present in Eoan, so I tried connecting that as well, but still no sound.

Does anyone else have this problem and more importantly does anyone have a solution? I want to use "Jitsi Meet" ([https://meet.jit.si](https://meet.jit.si)) for video conferencing, and it doesn't (yet) work very well in Firefox so I want to use Chromium for this.

---

