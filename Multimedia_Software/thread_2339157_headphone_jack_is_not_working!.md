---
title: "headphone jack is not working!"
date: 2016-10-05
forum: Multimedia Software
---

### Post by frozens on 2016-10-05
[http://www.alsa-project.org/db/?f=7127816ffd13cf58fd2982b7cc862314d8f4562a](http://www.alsa-project.org/db/?f=7127816ffd13cf58fd2982b7cc862314d8f4562a)
Here's my system and sound info.
I'm using laptop, and headphone jack is not working.

Mic jack and internal speaker(in laptop) are working well.

my sound card is [COLOR=#000000]Realtek ALC892.[/COLOR]

---

### Post by Bucky Ball on 2016-10-05
Welcome. Get Pulse Audio Volume Control installed if it isn't already (it's in the official repos so use whatever package manager you're using to install it). 

Play some music and launch PAVControl. Go to the 'Output' tab. You should see your audio stream running with the level meter bouncing up and down. Above that there is a 'port' drop-down list. Are your headphones listed on it? There should be (at least) two entries there: speakers and headphones.

---

### Post by Yellow Pasque on 2016-10-05
```
[    4.570436] snd_hda_codec_realtek hdaudioC1D0: ignore pin 0x1b with mismatching assoc# 0x3 vs 0x2
[    4.570493] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC892: line_outs=1 (0x17/0x0/0x0/0x0/0x0) type:line
[    4.570494] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=1 (0x14/0x0/0x0/0x0/0x0)
[    4.570495] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
```

hp_outs=0 is not good, but it may be because of the model=clevo option you added.
You should remove the model=clevo line you added to /etc/modprobe.d/alsa-base.conf and run the alsa info script again.

---

