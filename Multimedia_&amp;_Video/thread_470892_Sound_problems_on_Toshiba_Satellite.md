---
title: "Sound problems on Toshiba Satellite"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by barna on 2007-06-11
Hi
I have a Toshiba Satellite SA60-185, with an ATI IXP sound card. With Ubuntu 6.06 sound worked out-of-the-box, without any problems. 
After an upgrade to 7.04 I have several problems with sound:
- I don't manage to make my microphone work (correctly) After playing around with the settings in alsamixer (I don't know which was the key point) it finally began to produce some input to audacity, but when I play back the recorded sound, it plays in a very low voice (as if one would play back at a lower speed - but the playback speed is as it should be)
- I have compiled kino-1.0 (which worked perfectly under Ubuntu 6.06) - now it has problems with playback of sound: with the 'default' device, it produced no sound at all. If I changed the device to /dev/dsp, it produces some sound, but it is like a chirp.

Any idea what to check, what to change, etc?
(btw I am using the low-latency kernel, because midi players claimed they found no proper timer, and this was the suggested solution in some forums)

Thanks
Daniel

---

### Post by sudjatno on 2007-06-11
Have you tried looking at [https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam) ?
Godd documentation on tried and tested installation.

Cheers

---

### Post by barna on 2007-06-12
Hi
Thanks for the hint, I will have a look. 
With the sound output, the strange thing is that all other media players (kaffeine, amarok, mplayer) have perfect sound output. Kino 0.9.2 (shipped in Ubuntu 7.04) can also play sound. It is only kino 1.0, which has problems - and not always. Sometimes it produces good sound output, but then suddenly it breaks down, and begins to chirp. It used to work perfectly on Ubuntu 6.06

---

