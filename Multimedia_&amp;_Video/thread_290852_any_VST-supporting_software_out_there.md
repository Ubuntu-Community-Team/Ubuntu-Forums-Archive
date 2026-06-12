---
title: "any VST-supporting software out there?"
date: 2006-11-01
forum: Multimedia &amp; Video
---

### Post by mushroom on 2006-11-01
Any sequencers or anything like that that support VSTs?

---

### Post by bwanab on 2006-11-02
The short answer is yes, Rosegarden and om both support VST through DSSI. The long answer is that I don't really know how to make it work. The reason I know it can be done is that I use studio-to-go and I use it on that platform. I got DSSI compiled into 64Studio, but I haven't figured out how to get VST working there yet.

---

### Post by rytmisk on 2006-11-02
Ok - longer answer:

There is a deb package for fst in debian testing which worked for me a whie ago when I installed it during the testing phases of edgy - It's located at [http://packages.debian.org/unstable/sound/fst]("http://packages.debian.org/unstable/sound/fst")

If that works (requires wine at least) download a vst plugin ([http://www.greenoak.com/crystal/download.html](http://www.greenoak.com/crystal/download.html) works here) unzip it somewhere,start qjackqtl and then open a terminal and write ```
vsthost "path-to-vst..dll"
```

Good luck!
Ketil

---

### Post by mushroom on 2006-11-02
Ah, thanks for that.

---

