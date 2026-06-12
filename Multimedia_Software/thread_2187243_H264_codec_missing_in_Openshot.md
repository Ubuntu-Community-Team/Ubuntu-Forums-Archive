---
title: "H264 codec missing in Openshot"
date: 2013-11-11
forum: Multimedia Software
---

### Post by mabtifro2 on 2013-11-11
how can i install h264 codec to work in openshot? there are many video codecs, but that one is missing.

---

### Post by SeijiSensei on 2013-11-11
See if installing the [x264]("http://packages.ubuntu.com/search?keywords=x264") package helps.

---

### Post by mabtifro2 on 2013-11-11
just installed it. no luck.

[ATTACH=CONFIG]247765[/ATTACH]

---

### Post by SeijiSensei on 2013-11-11
Maybe you should ask in OpenShot support, then.

x264 is the open-source encoder for H.264, so if anything was going to provide this codec it would be that package.

---

### Post by dannyboy79 on 2013-11-11
did you scroll down? you won't see it shown named h264, it's x264 which is the open source equivalent to the commercially available codec h264. did you install the libavformat-extras-53 or whatever package it is? I had to install those in order to get h264 rendering to work in Kdenlive.

---

### Post by mabtifro2 on 2013-11-11
> **dannyboy79 said:**
> did you scroll down? you won't see it shown named h264, it's x264 which is the open source equivalent to the commercially available codec h264. did you install the libavformat-extras-53 or whatever package it is? I had to install those in order to get h264 rendering to work in Kdenlive.

danny thanks, no, i thought it would be named h264 alongside its brothers. i have libx264. i guess that's the one? damn. i should have realized it before. thanks.

---

