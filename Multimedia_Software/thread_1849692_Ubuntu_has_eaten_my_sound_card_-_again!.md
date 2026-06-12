---
title: "Ubuntu has eaten my sound card - again!"
date: 2011-09-25
forum: Multimedia Software
---

### Post by albert4545 on 2011-09-25
When I first started using Ubuntu (9.04) I could not find my sound card.
I upgraded to 11.04 today and were we are again.  So far the fixes recommended for use in terminal mostly come back telling me there's "no such file or directory.".

I'm stumped...

---

### Post by lidex on 2011-09-27
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

