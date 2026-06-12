---
title: "Static, Noise In Some Websites and Spotify"
date: 2020-09-23
forum: Multimedia Software
---

### Post by borsayt on 2020-09-23
I'm using a laptop with Ubuntu 20.04 and getting a buzzing noise when I play audio. You can hear it in this clip: [Example]("https://streamable.com/y0dmd2")
 
I used to get static noises on all flash video players, back when I  was running Windows and was able to fix it by installing another audio  driver.

 I always hear the noise at _Twitch.tv_, _Vimeo_; When I watch _YouTube_ videos I hear it sometimes, but not always.

 I hear the noise in _Spotify_ but it is much less pronounced and  sometimes goes away altogether. Often when I start playing music its all  clean and after some minutes the buzzing starts again.

 I checked alsamixer but when I slide the volume down sound is not audible.

 In my research I found a thread that suggested that ```
tsched=0
``` would help, but running that didn't make a difference.
 tried ```
pulseaudio -k
``` but pulseaudio wont restart again when i kill it
 

In alsamixer, chip and card is ;
```
Card: HDA Intel PCH      Chip: Realtek ALC269VB
```

Followed The Sticky Guides;
```
wget -O alsa-info.sh http://www.alsa-project.org/alsa-info.sh && chmod +x ./alsa-info.sh && ./alsa-info.sh
```

Output Was [This]("https://alsa-project.org/db/?f=2720352201ecde6dc917f27946f98e2bde530413") link

Edit:Notice something while playing music on spotify web, when i play music in ncspot (terminal add-on) most of the time there is no noise but when i tried browser versions it starts immediately.I can send more records of noise.

---

### Post by slickymaster on 2020-09-23
*Thread moved to **Multimedia Software**.*

---

### Post by dmuirhead on 2021-01-12
Try "killall speech-dispatcher". That works for me. Sometimes after a software update the static will start again but that command always stops it.

---

