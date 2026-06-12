---
title: "AC3 PassThrough not working"
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by whirly on 2006-06-06
Hi,

Some times ago I bought a Terratec Aureon sound card (modules used is snd-cmipci). I installed it in my breezy box, turn it on and then everything was working.

This week end I updgraded to dapper and now my AC3 passthrough is not working anymore. I get basic stereo sound through the spdif out but when I try to use the passthrough to get some dolby digital I get some errors message like this :

[FONT="Courier New"]ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.pcm.iec958.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM iec958:{CARD 0 AES0 0x02 AES1 0x82 AES2 0x00 AES3 0x02}
alsa-init: playback open error: No such file or directory
Could not open/initialize audio device -> no sound.
[/FONT]

The best I get was a short click on my amplifier and then the amplifier seems to shutdown the input as it interpret it as garbage.

I've upgraded the snd-cmipci module to v1.0.11 (the latest stable release from Alsa) but to no avail. So if somebody got an idea... I've also reports from oss that /dev/dsp is busy and when I try to aplay the device it is also "busy".

so if somebody encountered the same kind of problem well I am open to all suggestions.

---

