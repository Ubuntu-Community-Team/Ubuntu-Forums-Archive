---
title: "intel core i3 clarckdale and hdmi audio output"
date: 2010-05-03
forum: Multimedia Software
---

### Post by cybersplash on 2010-05-03
hi,

I install ubuntu 10.04 on my media center and I try to get sound over hdmi with no result.

I use core i3 integrated graphic card, I configure alsa mixer and I create a .asound file with appropriate output audio. I try to install pavucontrol an use speaker-test to play sound over hdmi audio. I never add error, my amp display that sound come over hdmi but no signal. I don't know if alsa support core i3 for hdmi audio.

This is the return of aplay -l command :
```

**** Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : ALC889 Analog [ALC889 Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 1 : ALC889 Digital [ALC889 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 3 : INTEL HDMI [INTEL HDMI]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
```

Could you explain me how to get sound over hdmi.

Thanks :)

PS : I don't speak english very well but in french forum I can't get response :) sorry.

---

### Post by khatkarrohit on 2010-05-07
I have the same problem. I am using INTEL DH57JG motherboard and i5-660 processor. I have samsung P2570HD monitor. I tried much but its still not working.

---

### Post by notanatheist on 2010-05-08
Should merge this with [http://ubuntuforums.org/showthread.php?t=1441955&highlight=DH57JG](http://ubuntuforums.org/showthread.php?t=1441955&highlight=DH57JG) and lock this one.

---

