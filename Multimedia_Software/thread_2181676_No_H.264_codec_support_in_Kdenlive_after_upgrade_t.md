---
title: "No H.264 codec support in Kdenlive after upgrade to 13.10"
date: 2013-10-18
forum: Multimedia Software
---

### Post by milo2 on 2013-10-18
Hi after upgrade from 13.04 to 13.10 Kdenlive would not render video with H.264 codec - libx264 -x264 (other codecs started rendering without this message):

"Rendering of /home/milo/kdenlive/123.mp4 crashed"
"WARNING: QApplication was not created in the main() thread." 

any ideas how to resolve it?

---

### Post by borgotretre on 2013-10-19
ubuntu saucy (or kubuntu or other derivatives from 13.10) on last upgrade (from rc or beta to stable) introduced a boring bug that affect many softwares. It have the library libx264 (from libavcodec) that give ever segfault error as noticed by different users with different computers

subscribe and check the bug on lauchpad for more information and to know when and how it will be fixed.

[https://bugs.launchpad.net/ubuntu/+source/libav/+bug/1241777](https://bugs.launchpad.net/ubuntu/+source/libav/+bug/1241777)

---

### Post by tzietz on 2013-10-22
I'm experiencing the same frustration. Hope this can be resolved soon. My production of video for my school has ground to a halt.

---

### Post by vanadium on 2013-10-23
Glad I see this thread. Indeed: no H264 on Ubuntu 13.10, it seams.

---

### Post by dannyboy79 on 2013-10-23
hence why i stay with rock solid 12.04.3, my kdenlive is still working great.

---

### Post by ben-blankley on 2013-11-04
Your experience may vary (as I got a different error message), but I was able to restore x264, mp3, and other support in KDEnlive by following this howto after upgrading from 13.04 to 13.10.

I only ended up doing this part:

"Open up your file manager of choice and navigate to **&#8220;/home/.kde/share/config/&#8221;**. Look for a file named **kdenliverc** and delete it [...] Close the file manager window."

[http://geekwith.us/how-to-fix-the-unsupported-codec-problem-in-kdenlive/](http://geekwith.us/how-to-fix-the-unsupported-codec-problem-in-kdenlive/)

---

### Post by vanadium on 2013-11-04
I did not try yet, but saturday, an update of H264 was pushed: I suppose that H264 encoding will now work again.

---

