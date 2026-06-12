---
title: "Converting rmvb files"
date: 2010-01-12
forum: Multimedia Software
---

### Post by aliciapg on 2010-01-12
I am trying to figure out how to convert rmvb files to anything else because the video editors I use do not support them (Avidemux and Kdenlive). Or at least they don't seem to support them.

Anyways, I've figured out how to convert them, but the videos are all low-quality. I have a very high-quality rmvb file and I want to keep the quality of the video as high as possible. I know I will lose some quality, but my current method loses a _lot_. Any suggestions?

---

### Post by s.fox on 2010-01-12
Hello,

What method are you currently using to convert them?

I found [this]("http://ubuntuforums.org/showthread.php?t=1066670") post from a while back which gives some instructions to follow.  No idea what the quality will be like though.  Sorry.

-Silver Fox

---

### Post by aliciapg on 2010-01-12
I tried mencoder and winff. I'm currently trying handbrake by someone's suggestion. I'm thinking about ffmpeg next if that can handle rmvb files.

---

### Post by drobi on 2010-01-14
Try the Format Factory (windows version) from wine.

---

### Post by paul.gevers on 2010-01-15
> **aliciapg said:**
> I tried mencoder and winff. I'm currently trying handbrake by someone's suggestion. I'm thinking about ffmpeg next if that can handle rmvb files.

Winff is a GUI for ffmpeg, so that is basically the same. Probably your problem is that the preset (at least for Winff) is specifying a lower quality than you want. The same goes for memcoder. So what codec/container do you want to transcode? And what does codec is in the rmvb container? Maybe you don't need to transcode, just put it in a different container. In order to help we need more information thou.

---

### Post by aliciapg on 2011-04-01
I'm not really sure how to find out that information. Where could I look?

I just want to convert it to something usable. Using a newer version of kdenlive "supports" rmvb, but I can't actually get it to render correctly. So converting it is still my only choice. :/

---

