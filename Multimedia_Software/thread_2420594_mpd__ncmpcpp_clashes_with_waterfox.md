---
title: "mpd / ncmpcpp clashes with waterfox"
date: 2019-06-07
forum: Multimedia Software
---

### Post by Furycd001 on 2019-06-07
HI

If I open any media in [waterfox]("https://www.waterfox.net/") (youtube, twitch etc) then I cannot play music though ncmpcpp until I close waterfox. How can I stop this from happening ?? I run mpd as user instead of service. Also I cannot seem to get the visualizer in ncmpcpp to work. Here is my [mpd config]("https://termbin.com/914r") && [ncmpcpp config.]("https://termbin.com/3dh6") Many thanks in advanced for your help....

---

### Post by Yellow Pasque on 2019-06-08
You have mpd set to use the hardware device (alsa output hw:0,0). If another program is playing sound, then pulseaudio has exclusive access to the hardware device.
In other words, try setting mpd to use pulse output.

---

### Post by Furycd001 on 2019-06-10
> **Yellow Pasque said:**
> You have mpd set to use the hardware device (alsa output hw:0,0). If another program is playing sound, then pulseaudio has exclusive access to the hardware device.
In other words, try setting mpd to use pulse output.

Ok thank you for the heads up :)

---

