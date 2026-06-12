---
title: "pinnacle pctv stick and noisy sound"
date: 2007-02-13
forum: Multimedia &amp; Video
---

### Post by mikea87 on 2007-02-13
I have pinnacle pctv hybrid pro stick. I use xawtv to watch analogue tv. To redirect sound I use:

```
sox -r 48000 -w -c 2 -t ossdsp /dev/audio1 -t ossdsp /dev/audio

```

But sound isn't clear. There is annoying noise. It isn't fault of signal because in windows everything is ok. How reduce or delete this noise? Decreasing volume does really little.

---

