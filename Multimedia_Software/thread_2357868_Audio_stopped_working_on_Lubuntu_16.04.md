---
title: "Audio stopped working on Lubuntu 16.04"
date: 2017-04-06
forum: Multimedia Software
---

### Post by brunocassol on 2017-04-06
Hi,
I installed Lubuntu 16.04 yesterday. The headset sound worked after editing /usr/share/alsa/alsa.conf with:

```
defaults.ctl.card 2
defaults.pcm.card 2

```

It worked fine for a couple of reboots. 
But now during user/password input it plays a noise sound for a brief second then stops.
I also can no longer see the speaker icon on tray even when I mark right click -> indicator applets -> sound menu.

This is my ALSA debug: [http://www.alsa-project.org/db/?f=423aa5819190a7ea73cf53b8320b89b70f1b7c91](http://www.alsa-project.org/db/?f=423aa5819190a7ea73cf53b8320b89b70f1b7c91)

This successfully plays noise on my headset:

```
speaker-test -Dsysdefault:CARD=Headset
```

Please help.

---

### Post by brunocassol on 2017-04-06
Fixed by using pulseaudio:

```
sudo apt-get install pulseaudio pavucontrol && pavucontrol
```

Then disabled all sound devices but my headset. Didn't even needed to restart.

---

