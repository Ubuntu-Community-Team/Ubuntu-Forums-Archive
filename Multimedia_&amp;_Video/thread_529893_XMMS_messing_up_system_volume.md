---
title: "XMMS messing up system volume?"
date: 2007-08-19
forum: Multimedia &amp; Video
---

### Post by Virgofenix on 2007-08-19
Am I the only person having this problem with XMMS (and apparently, Beep)?

XMMS' volume control doesn't just control the volume on the player, but the volume on my whole system. I verified  this by playing mp3's on Exaile and XMMS at the same time. Both were on max volume. When I lowered the volume on XMMS, Exaile's volume also dropped. The volume indicator on Exaile didn't move however. In fact, I could still lower Exaile's volume using its own controls. However, the maximum volume seems to be controlled by XMMS. Even if I set Exaile at max volume, If XMMS was mute, Exaile didn't give any sounds. In fact, my whole system would be mute. This problem isn't just isolated to Exaile. XMMS also suppresses the sound in all my other applications: games like Neverwinter Nights or videos in Youtube. And I've had this problem in KDE, GNOME, and Enlightenment.

---

### Post by kevinlyfellow on 2007-08-19
Yeah, xmms is an old program that was developed when you could only play one noise at one time.  Naturally they didn't care if it hijacked the sound or not.  If someone knows a solution, I'd be interested because the same thing happens with xine-ui

---

### Post by Virgofenix on 2007-10-21
The volume control in XMMS changes the PCM in Volume Control. I'm using GNOME and I'm not aware of using xine. On the other hand, my volume gets changed every now and then, and I'm no longer using XMMS. Maybe I have another program hijacking my PCM control?

---

### Post by tgalati4 on 2007-10-21
You can select the sound system in XMMS.  OSS is an older sound architecture, ALSA is a newer sound architecture.  ALSA mixes sounds from multiple applications.

In the Volume mixer control, you can normally specify which channel gets adjusted by the master volume control.  It could be PCM, Headphone, Speaker, Master, Mono.  You may need to experiment a bit to figure out which control gets throttled by your multi-media keys.  Each application that uses sound behaves a little differently.

---

