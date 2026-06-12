---
title: "How do I even figure out what my soundcard is?"
date: 2006-09-01
forum: Multimedia &amp; Video
---

### Post by Hyphessobrycon on 2006-09-01
I have an old windows 98 SE IBM Aptiva PC. I have no sound, and have tried some of the things mentioned on this forum, but they all require knowledge of one thing (or so it appears to my ignorant self): you seem to have to know at least what your sound card is before you can configure it. I couldn't find anything on google for my PC model (IBM aptiva s series 631-really old), but I might have read somewhere that the sound card is built into the motherboard, whatever that means. I am not sure what I should do. If you want me to run any UNIX commands, I'll try and do so ASAP and post the output immediately.

---

### Post by ciscosurfer on 2006-09-02
Try checking the output of```
lspci | grep audio
```and see if that helps.

---

