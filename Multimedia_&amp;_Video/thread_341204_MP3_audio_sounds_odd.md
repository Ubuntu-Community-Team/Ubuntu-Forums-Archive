---
title: "MP3 audio sounds odd"
date: 2007-01-18
forum: Multimedia &amp; Video
---

### Post by Enigmatic on 2007-01-18
I built a Ubuntu Edgy machine for a guy, and I tested the sound before sending it off, and it sounded fine, but I never listened to any MP3s. 

He says the system sounds are fine, but any MP3s sound like they're being played in slow motion. He's tried different programs too.

Any ideas what might cause this? Sounds pretty odd to me, but I haven't been able to listen to it myself.

---

### Post by pertti on 2007-01-19
If all the players he has tried are GStreamer-based (e.g. Totem and Rhythmbox), it could be due to the 'gstreamer0.10-fluendo-mp3' package (it gave me bad sound quality, but no slow-mo, though). Uninstall it, make sure 'gstreamer0.10-plugins-ugly' (or the multiverse one, i'm not sure) is installed, and try again.

Altough if this problems happens with other kind of players, such as Xmms or Mplayer, then the above is not going to fix it.

---

### Post by Lord Illidan on 2007-01-19
Is dma enabled?

```
sudo hdparm /dev/hd*
``` should give you information whether it is enabled or not.

---

### Post by Enigmatic on 2007-01-22
Well, he's tried all of those. DMA was on, fluendo he uninstalled, made sure all the -ugly packages were installed, rebooted and even tried XMMS.

I'm hoping it's not the sound card.

---

### Post by ride1226 on 2007-01-22
i am having the exact same problems...my system sounds and everything are crystal clear however when playing my mp3s through amaroK they sounds slow mo scretched out unclear like...if that makes sence...im on 6.06 however. but same problem. ill try the above if i can figure all that out.

---

### Post by ride1226 on 2007-01-22
tried the above mentioned and played in amaroK and rythmbox and its still the same.

---

