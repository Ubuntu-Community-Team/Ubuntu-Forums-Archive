---
title: "Sound not Working suddenly"
date: 2006-12-27
forum: Multimedia &amp; Video
---

### Post by gmatt on 2006-12-27
Umm, well the title describes the problem and I can't really describe anything more... I have no idea what might have happened sound was working fine one minute the next its dead silent and nothing I can do can fix it.... 

How do I even start diagnosing what the problem might be here? Any suggestions?

---

### Post by kerry_s on 2006-12-27
Make sure your not muted. Also i noticed on mine i didn't have esound & esound-client installed so i didn't have sound in gaim.

---

### Post by gmatt on 2006-12-27
Well, I'm not sure what I did, but I used ```
alsamixer
``` to enable PCM by pressing the M key. For some reason it was off. It seems to have made my sound working again. Weird, whatever happened, it was truly paradoxal to me.

---

### Post by kerry_s on 2006-12-27
That means some how you mistakenly muted it. PCM is actually the main volume, it is used in the applications like xmms,mplayer,totem,...You might have muted it in a app, thus muting your whole system.

---

