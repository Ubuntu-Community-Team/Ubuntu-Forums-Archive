---
title: "volume settings not staying in alsamixer"
date: 2009-05-17
forum: Mythbuntu
---

### Post by mark467 on 2009-05-17
i have to turn up master and pcm everytime i go to watch live tv in alsamixer. the settings wont stick what am i missing?

---

### Post by ajgreeny on 2009-05-17
What application are you using to watch TV?  If you are using smplayer, and perhaps therefore also mplayer and gmplayer, I know you need to set that to use software volume control, otherwise the volume levels are set automatically to whatever is set in smplayer.  It took me a while to find this and I only did so by accident, just trying all posibilities.  If you use another player, look for something similar in their preferences.

---

### Post by kerry_s on 2009-05-17
> **mark467 said:**
> i have to turn up master and pcm everytime i go to watch live tv in alsamixer. the settings wont stick what am i missing?

did you run>** sudo alsaconf**

---

### Post by mark467 on 2009-05-18
Thanks, that was it....

---

