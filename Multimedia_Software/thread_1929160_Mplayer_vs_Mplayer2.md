---
title: "Mplayer vs Mplayer2"
date: 2012-02-21
forum: Multimedia Software
---

### Post by vikrant82 on 2012-02-21
I was comparing quality/performance of mplayer 2:1.0~svn34707-1~precise with mplayer2 - mplayer2-2.0-linux-x86_64-glibc211.tar.bz2

Using flags as: ```
mplayer? -vo vdpau -ao alsa -benchmark
```

I am testing with a video segment.

With mplayer2 I get:
```
BENCHMARKs: VC:   0.401s VO:   5.066s A:   0.533s Sys:  23.239s =   29.238s
BENCHMARK%: VC:  1.3704% VO: 17.3253% A:  1.8231% Sys: 79.4812% = 100.0000%
```

With mplayer I get:
```
BENCHMARKs: VC:   3.056s VO:   0.644s A:   0.332s Sys:  15.903s =   19.935s
BENCHMARK%: VC: 15.3276% VO:  3.2316% A:  1.6635% Sys: 79.7773% = 100.0000%
```

First, how should these numbers be read. I can see that mplayer takes around 19.94s compared to 29.24s. But what are VC, VO etc?

Does this mean mplayer2 is slower on this machine ?
This is a i7 2630QM sandy , with Nvidia GTX560M. I am on nvidia - 295.20-0ubuntu1~xedgers~precise1

---

