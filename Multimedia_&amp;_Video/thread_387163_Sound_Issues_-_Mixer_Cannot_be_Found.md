---
title: "Sound Issues - Mixer Cannot be Found"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by apauld on 2007-03-18
Hello, 

Sound works with live Edgy boot and fresh install. After kernel upgrade to 2.6.17-11, sound no longer works.

kmix reports Mixer Cannon Be Found, and

```
adix@hummer:~$ aplay -l
aplay: device_list:222: no soundcards found...
```

All the correct modules seem to be loaded but the (what appears to be) minor changes from live to install boot have been posted below.


I have tried:
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

Any help would be greatly appreciated. Thank you! Aaron


Sound config (modprobe | grep snd, cat /proc/asound/cards, cat /dev/sndstat)  from live boot:


```

snd_ens1371            28704  3
gameport               17160  1 snd_ens1371
snd_rawmidi            27264  1 snd_ens1371
snd_seq_device          9868  1 snd_rawmidi
snd_ac97_codec         97696  1 snd_ens1371
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  4 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  2 snd_pcm
snd                    58372  12 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  1 snd_pcm

 0 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                      Ensoniq AudioPCI ENS1371 at 0xd400, irq 201

Sound Driver:3.8.1a-980706 (ALSA v1.0.12rc1 emulation code)
Kernel: Linux ubuntu 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
Ensoniq AudioPCI ENS1371 at 0xd400, irq 201

Audio devices:
0: ES1371 DAC2/ADC (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: ES1371

Timers:
31: system timer

Mixers:
0: TriTech TR28602

```

And after install & upgrade:
```

snd_ens1371            28704  0
gameport               17160  1 snd_ens1371
snd_rawmidi            27264  1 snd_ens1371
snd_seq_device          9868  1 snd_rawmidi
snd_ac97_codec         97696  1 snd_ens1371
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  1 snd_pcm

 0 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                      Ensoniq AudioPCI ENS1371 at 0xd400, irq 201


Sound Driver:3.8.1a-980706 (ALSA v1.0.12rc1 emulation code)
Kernel: Linux hummer 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
Ensoniq AudioPCI ENS1371 at 0xd400, irq 201

Audio devices:
0: ES1371 DAC2/ADC (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: ES1371

Timers:
31: system timer

Mixers:
0: TriTech TR28602

```

---

### Post by apauld on 2007-03-20
Quick follow up Just in case anyone else does something silly like I did:

I removed groups that I 'thought' I didn't need. Audio group is there for a reason!

Thanks! Aaron

---

### Post by AchimRS on 2007-09-30
bump

---

### Post by ubuntunewb75 on 2007-10-20
I am also having this problem--all is installed, but no sound HDA INTEL 8000 rev 3 series on the motherboard..

---

### Post by tau_neutrino on 2007-12-05
I have same issue. I have HDA Intel on ASUS motherboard.

Tried to compile ALSA drivers manually. Didn't work.

I think only full reinstall of ubuntu will fix the problem.

---

