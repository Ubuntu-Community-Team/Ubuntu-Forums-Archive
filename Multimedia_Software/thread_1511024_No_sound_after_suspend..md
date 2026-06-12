---
title: "No sound after suspend."
date: 2010-06-16
forum: Multimedia Software
---

### Post by konradmb on 2010-06-16
I experience no sound after suspend and resume on Toshiba satellite p100. Mute and unmute, sudo alsa force-reload, add "options snd-hda-intel model=toshiba" to alsa-base.conf and delete ~/.pulse do not work for me. I use lucid. Attached pulseaudio -vvvv logs. Only I experience this?

---

### Post by konradmb on 2010-06-18
bump

---

### Post by dsm83 on 2010-06-19
Try:

sudo alsactl init 0

---

### Post by konradmb on 2010-06-20
This don't work for me, I still can't hear any sound after suspend. Here is output:
```
konrad@konrad-laptop:~$ sudo alsactl init 0
[sudo] password for konrad: 
Unknown hardware: "HDA-Intel" "Conexant CX20551 (Waikiki)" "HDA:14f15047,1179ff31,00100000" "0x1179" "0xff31"
Hardware is initialized using a guess method

```

---

### Post by lkjoel on 2010-06-21
Click on [Fix your sound!]("https://help.ubuntu.com/community/OpenSound") in my sig.
That should fix it.

Let me know if it works!

---

