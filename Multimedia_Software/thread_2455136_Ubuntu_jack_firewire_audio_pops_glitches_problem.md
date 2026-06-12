---
title: "Ubuntu jack firewire audio pops glitches problem"
date: 2020-12-13
forum: Multimedia Software
---

### Post by zanox on 2020-12-13
Hi to all, here's a solution:

```
sudo usermod -a -G audio username
```
```
sudo gedit /etc/modprobe.d/blacklist.snd.conf
```
(use gedit or mousepad or nano or whatever you want)
insert ```
blacklist snd-dice
``` in the empty file

then run jack with firewire module (not alsa)

also install jack module sink for pulseaudio (search "jack sink" in synaptic)

---

