---
title: "[SOLVED] Conflit with ffmpeg and mplayer"
date: 2008-08-02
forum: Multimedia Software
---

### Post by jevharr on 2008-08-02
When I try to install these, I am getting a message that there is a conflict or I am creating an impossible situation. I can install one, but when I go to install the next, it says that the other will be removed. The piece that seems to be causing the trouble is libmp3lame0 vs liblame0. Does anyone have these installed together? Why am I having this trouble?

---

### Post by jevharr on 2008-08-04
I resolved this conflict by removing all of the software depending on libmp3lame0 and liblame0 and then re-installing at the same time using apt-get install ffmpeg mplayer

---

