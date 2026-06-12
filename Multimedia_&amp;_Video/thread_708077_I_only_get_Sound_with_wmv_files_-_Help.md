---
title: "I only get Sound with wmv files - Help"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by jubei52 on 2008-02-26
Hello.

I am new to ubunto but I have transferred my video files and I can see any vide for the .wmv files although I hear sound.

I looked at all the other instructions but I could not understand them or I tried them and they didn't work!  

I am using Ubuntu 6.06 LTS with Intel P4 2.8 Ghz, 1 GB RAM, ATI Radeon 9200.  

Thanks in advance

---

### Post by erginemr on 2008-02-26
I believe you should enable the Medibuntu repository:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

and then install w32codecs to be able to view wmv files.

Installing gstreamer bad and ugly codecs from synaptic will also help you play more video file types:
```
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
```

---

