---
title: "low volume"
date: 2009-05-08
forum: Multimedia Software
---

### Post by Insomniac20k on 2009-05-08
The volume on this machine is really really low. When windows was on the machine, it was a lot louder.

I just got songbird working and I really like it, but it's useless because I can barely hear the music with headphones on. I can use VLC, because for some reason it amplifies like 200 percent but VLC doesn't have much going for it feature wise.

Any one got a work around for me? I'm thinking it might be a driver issue, but if I go under Sound Preferences, it recognizes my exact sound card, which is an integrated HDA nVidia ALC662

Thanks for your help!

Matt

---

### Post by akudewan on 2009-05-24
I have the same problem. I have tried adding the line:
```

options snd-hda-intel model=3stack-dig

```
to the /etc/modprobe.d/alsa-base.conf file. And also tried many other models, but nothing gets the sound volume to a proper level. Its quite frustrating...

---

