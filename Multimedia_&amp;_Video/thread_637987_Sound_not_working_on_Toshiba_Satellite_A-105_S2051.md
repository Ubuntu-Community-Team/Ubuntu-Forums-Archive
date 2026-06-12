---
title: "Sound not working on Toshiba Satellite A-105 S2051"
date: 2007-12-11
forum: Multimedia &amp; Video
---

### Post by TonkaTruck18 on 2007-12-11
Hi I just installed Ubuntu 7.10 on a Toshiba Satellite A-105 S2051 and the sound isn't working it is not on mute and i have fiddled with the preferences and it still doesnt work. Your help will be greatly appreciated thanks!! :)

---

### Post by spec456 on 2007-12-15
What sound card do you have? 

Applications > Accessories > Terminal

Then type:

```
lpsci | grep -i audio
```

If you have an intel HDA sound card, then type in the terminal:

```
sudo gedit /etc/modprobe.d/alsa-base
```

Then at scroll down and at the end add:

```
options snd-hda-intel model=3stack
```

Then save and restart your computer and the sound should work. Let me know how it goes.

---

