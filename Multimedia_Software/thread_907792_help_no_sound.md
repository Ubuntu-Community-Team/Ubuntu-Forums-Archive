---
title: "help no sound"
date: 2008-09-01
forum: Multimedia Software
---

### Post by Breakar on 2008-09-01
i have virtualbox i couldnt get sound on, i was talkin to my friend how to get it to work he said change device to OSS in both ubuntu and virtualbox so i did that now i dont have sound.

I changed it back to originally what it was alsa but still no sound! :confused:

---

### Post by tuxxy on 2008-09-01
ALSA for both should work

---

### Post by edvar on 2008-09-01
I keep loosing all sound at least once a week. Every time it happens I have to:

$ sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
$ sudo init 6
$ sudo apt-get install alsa-base alsa-utils fast-user-switch-applet gdm gdm-themes kubuntu-kde4-desktop linux-sound-base
$ sudo init 6

After that I have my digital sound back.

This is really annoying... However it's just a temporary fix as I'll have the same problem a couple of days later.

I'm using ALSA. Uninstalled PulseAudio.

---

### Post by Breakar on 2008-09-01
does that work in gnome or just kde? everytime i try right click on the speaker in the panel bar it freezes my computer so i have to reboot.

---

### Post by Hyper Tails on 2008-09-01
I have the same problem to in kubuntu

i got sound nofications but no sound in other software

---

### Post by Breakar on 2008-09-01
I got sound back by resetting it with this

```
sudo /etc/init.d/alsa-utils restart
```

then going to system>sound and change "auto detect" to alsa and it worked.

---

