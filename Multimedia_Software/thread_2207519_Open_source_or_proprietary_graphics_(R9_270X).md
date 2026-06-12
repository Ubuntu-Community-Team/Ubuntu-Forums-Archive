---
title: "Open source or proprietary graphics (R9 270X)"
date: 2014-02-23
forum: Multimedia Software
---

### Post by tmette on 2014-02-23
Hey guys so far the open source drivers are working great for my card. However, the sound isn't working on HDMI. I'm hoping to start playing some games on Steam also since they have started to support quite a bit of games. My question is, should I just install the proprietary graphics for Ubuntu 13.10? Will it fix the sound issue? I'm sort of hesitant to use the ATI drivers because in the past, watching Youtube videos would sometimes glitch real badly, and I would get horizontal lines while watching videos in SMplayer or VLC. Any advice?

---

### Post by Bucky Ball on 2014-02-24
If you're intending to game you are probably going to need the proprietary drivers. Unsure how a graphics driver is going to effect sound, though ... :-k

---

### Post by Yellow Pasque on 2014-02-24
If using open-source driver, you have to manually enable HDMI sound because it was not enabled by default until kernel 3.13 (though I don't know if it will work for R9 series with stock Saucy kernel)

[https://help.ubuntu.com/community/RadeonDriver#HDMI_Audio](https://help.ubuntu.com/community/RadeonDriver#HDMI_Audio)

Turning on DPM may help too.

---

### Post by tmette on 2014-02-24
> **Temüjin said:**
> If using open-source driver, you have to manually enable HDMI sound because it was not enabled by default until kernel 3.13 (though I don't know if it will work for R9 series with stock Saucy kernel)

[https://help.ubuntu.com/community/RadeonDriver#HDMI_Audio](https://help.ubuntu.com/community/RadeonDriver#HDMI_Audio)

Turning on DPM may help too.


Thank you! I will try this!

---

