---
title: "Rhythmbox can't play today"
date: 2010-01-20
forum: Multimedia Software
---

### Post by Colin@oxford on 2010-01-20
I was using Rhythmbox successfully yesterday.  This morning the automatic updates said I should install some new packages, one of which was, I think, rhythmbox.  Now it tells me that "The autoaudiosink element is missing" whenever I try to play something. What do I need to do in order for rhythmbox to work again?
Other audio programs, e.g. Audacity, work fine.

---

### Post by Yellow Pasque on 2010-01-20
Does audio output work properly in this dialog?:
```
gstreamer-properties
```

---

### Post by Colin@oxford on 2010-01-21
It didn't when I first brought it up (set to OSS).  When I changed to ALSA, the test worked but Rythmbox still did not.  When I changed to "auto detect" everything worked OK.

I wonder what changed it.

Thanks.

---

### Post by Colin@oxford on 2010-01-21
Hmm.  Seem intermittent.  After a reboot, I started rhythmbox again and had the same error.  Looked at gstream-properties and they were still set to "autodetect" and the test sound weas OK.  Killed & restarted rhythmbox and all was OK again.  Very strange.

---

