---
title: "HDMI ac3 passthough audio"
date: 2009-02-08
forum: Mythbuntu
---

### Post by jape42 on 2009-02-08
Hi All,

After I got some help from the radeonhd driver list, I am now able to play ac3 audio over HDMI with mplayer via a command line like this:

 mplayer -ac hwac3 -ao alsa:device=iec958=1 -vo xv -fs 2041_20090208074700.mpg

Can anyone help me figure out what the equivalent settings under mythtv would be?  Obviously I've tried a few variations, but the best I can get is clicky static.

regards,

jp

---

### Post by jape42 on 2009-02-11
> **jape42 said:**
> Hi All,

After I got some help from the radeonhd driver list, I am now able to play ac3 audio over HDMI with mplayer via a command line like this:

 mplayer -ac hwac3 -ao alsa:device=iec958=1 -vo xv -fs 2041_20090208074700.mpg

Can anyone help me figure out what the equivalent settings under mythtv would be?  Obviously I've tried a few variations, but the best I can get is clicky static.

regards,

jp


Oddly enough, these simple settings worked:

Audio output device: ALSA:iec958
Passthrough output device: ALSA:iec958:{ AES0 0x02 }
Max Audio Channels: Stereo
Upmix: passive
Enable AC3 to SPDIF passthrough: on
Enable DTS to SPDIF passthrough: on
Aggressive soundcard buffering: off
Use internal volume controls: off


jp

---

