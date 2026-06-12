---
title: "Suddenly low volume"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by feedmecereal on 2007-12-17
I'm using a Dell Dimension E520 that came with Ubuntu 7.04 installed. I upgraded to 7.10 just fine and my sound worked fine for a long time. Recently, the volume on my computer seems to be too low. This is true in every application I have tried such as Totem, VLC, Firefox, etc. It is not extremely low because all I have to do is turn up the volume on my speakers and everything is fine. But I would rather the volume was back to where it was before.

I have the volume control bar turned all the way up and I have it all the way up in Totem.

---

### Post by Pauan on 2007-12-25
Try opening a command line and typing in "alsamixer". Now turn the "PCM" setting to 100. Does that help any?

---

### Post by feedmecereal on 2007-12-25
Thanks, that fixed it. I'm not sure what turned down the volume in the first place.

---

### Post by Pauan on 2007-12-25
I had the same problem. Apparently certain programs mess with the audio, specifically the PCM setting. This can happen if a program changes the volume then crashes or "forgets" to fix the volume back to normal again. In my case it was a problem with a crashing audio program.

---

