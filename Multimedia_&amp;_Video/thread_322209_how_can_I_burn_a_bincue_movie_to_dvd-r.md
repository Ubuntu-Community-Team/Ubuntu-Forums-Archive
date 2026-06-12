---
title: "how can I burn a bin/cue movie to dvd-r?"
date: 2006-12-20
forum: Multimedia &amp; Video
---

### Post by bionnaki on 2006-12-20
hello. I have a movie in bin/cue format. how can I burn this to dvd? thanks

---

### Post by Orval on 2006-12-20
K3B should support it. And otherwise, use

> 
cdrdao write --device /dev/hdc image.cue


replace image.cue with your filename and /dev/hdc with your dvd device.

---

### Post by bionnaki on 2006-12-21
thanks. k3b doesnt support it. and cdrdao said the file was too large even though the bin/cue was 700mb max. I also tried bchunk - it worked but viewing the .iso's was choppy and the sound was distorted.

hmm. there's got to be a better way

---

### Post by Orval on 2007-01-05
k3b does support it, I tried it yesterday. You have to go to "burn iso" and then select the bin file.

---

### Post by toolazy2work on 2007-02-01
gnomebaker also will burn bin/cues, just select burn iso and select the cue file

---

