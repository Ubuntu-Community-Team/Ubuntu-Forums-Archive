---
title: "Enabling external soundcard (audigy ZS)"
date: 2008-04-26
forum: Multimedia Software
---

### Post by cumulonix on 2008-04-26
My onboard sound card doesn't work; so I use Creative Audigy 2 ZS Notebook with my laptop (Toshiba). I could play sound on Movie Player, but mplayer, real player, firefox (youtube and other flash sound) would not play.
here is what i did to make things work
1)```
lsmod | grep snd 
``` to list sound modules used.
2) Blacklist omboard sound modules in /etc/modprobe.d/blacklist```
 sudo gedit /etc/modprobe.d/blacklist
```
here is what i did```

#blacklists onboard soundcard. 26th april 2008
blacklist snd_intel8x0
blacklist snd_ac97_codec
blacklist snd_ac97_bus
```
3)Reboot.

---

### Post by refai on 2008-05-29
> **cumulonix said:**
> My onboard sound card doesn't work; so I use Creative Audigy 2 ZS Notebook with my laptop (Toshiba). I could play sound on Movie Player, but mplayer, real player, firefox (youtube and other flash sound) would not play.
here is what i did to make things work
1)```
lsmod | grep snd 
``` to list sound modules used.
2) Blacklist omboard sound modules in /etc/modprobe.d/blacklist```
 sudo gedit /etc/modprobe.d/blacklist
```
here is what i did```

#blacklists onboard soundcard. 26th april 2008
blacklist snd_intel8x0
blacklist snd_ac97_codec
blacklist snd_ac97_bus
```
3)Reboot.

thanks for the input any clues of getting the mic to work ?

---

