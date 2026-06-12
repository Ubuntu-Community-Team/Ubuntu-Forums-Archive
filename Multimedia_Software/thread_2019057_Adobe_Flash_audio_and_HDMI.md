---
title: "Adobe Flash audio and HDMI"
date: 2012-07-07
forum: Multimedia Software
---

### Post by w1ll1am on 2012-07-07
Okay I have been using an nvidia hdmi card with mythtv and flashplayer for hulu/amazon prime/youtube for about a month now with no problems. Yesterday after a reboot audio no longer works. I have pulse audio volume control installed and it shows that I have flash configured for HDMI out. I have an .asoundrc file in my home folder that initially got audio to work with flash.

```
 
pcm.!default {
type hw
card 1
}

ctl.!default {
type hw
card 1
}

```

I have reinstalled flash and I have deleted and recreated the .asoundrc file. 

PLEASE can someone help me I have tried everything that I know of and I can't watch anything with flash.

---

### Post by w1ll1am on 2012-07-08
bump

---

### Post by pqwoerituytrueiwoq on 2012-07-08
i am using this:
```
cat /etc/asound.conf 
pcm.pulse {
type pulse
}
ctl.pulse {
type pulse
}
pcm.!default {
type pulse
}
ctl.!default {
type pulse
}

```
make sure sound is working on hdmi if not check the setting under pulse audio prefs

---

### Post by w1ll1am on 2012-07-09
I tried that as well and it didn't work. I get sound from HDMI when I am playing a movie it is only when flash is being used.

---

### Post by w1ll1am on 2012-07-09
I have my / installed to a separate drive from my media drives so I reinstalled and set everything to the way it was before the reinstall and now everything works fine.

I do not consider this a fix but unfortunately I don't want to just wait and not be able to use my system.Thanks.

---

