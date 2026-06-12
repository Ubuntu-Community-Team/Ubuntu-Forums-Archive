---
title: "Join video and audio with mencoder"
date: 2006-11-18
forum: Multimedia &amp; Video
---

### Post by Patskumaster on 2006-11-18
Hey!

I don't sure is this right area, but I hope.

Can I join audio and video files together with Mencoder? Is this possible?

Thank's

---

### Post by whatever on 2006-11-18
yes

---

### Post by Patskumaster on 2006-11-18
Could you tell how?

---

### Post by whatever on 2006-11-18
mencoder video.avi -audiofile audio.mp3 -ovc copy -oac copy -o output.avi

---

### Post by Patskumaster on 2006-11-18
It works fine. Thank you!

---

