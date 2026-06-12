---
title: "sound stopped working"
date: 2010-11-20
forum: Multimedia Software
---

### Post by me.translucent on 2010-11-20
i am using ubuntu 10.10 and my sound stopped woking .it had happened before and i had a vague recollection that reinstalling some thing worked so i did a 
```

      sudo apt-get purge pulseaudio
      sudo apt-get install pulseaudio
      sudo apt-get purge alsa
      sudo apt-get install also

```

but now even the volume controll icon is gone . 
btw i also tried this later 
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils

```
which i think was the thing that worked last time , but still the sound is not coming .

---

### Post by me.translucent on 2010-11-20
update : i tried alsamixer c0 and increased the volume of my speaker(which was set to zero ) now everything seems to workfine except rhythmbox and the volme controll option is still missing.

---

### Post by me.translucent on 2010-11-20
that too fixed with <code>sudo apt-get install indicator-sound</code>
ps : had to do again <code> alsamixer -c0 </code> and increase the voulme
*wonders why the sound goes back to zero* 
%and of course there were rebooots too%

---

