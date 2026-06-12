---
title: "Audio plays about 50% too fast"
date: 2006-12-18
forum: Multimedia &amp; Video
---

### Post by hanman on 2006-12-18
I've been using Kubuntu Edgy for about a week now, and I really like it so far.  I migrated after a couple of years from Gentoo.  Everything has worked great except for my sound.  Any audio i play is too fast.  As in, it sounds like the Chipmunks, more or less.  I tried WMA, OGG, and M4A.  I played them with AmaroK, Kaffeine (both of which use xine), and XMMS.  It does the same thing in all programs with one exception: in AmaroK and Kaffeine, it also skips every 2 seconds or so.  In XMMS, i tried to set it to ALSA, aRts, and OSS output, all of which give the same "chipmunk" sound.

Here is my lsmod | grep snd :

```

[FONT="Impact"]snd_intel8x0           34844  2
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0
snd_mixer_oss          19584  2 snd_pcm_oss
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  2 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm[/FONT]

```

My computer has an Intel 82801BA-ICH2 chipset with on board audio.  In the system settings, i have it set to use ALSA instead of autodetect, but either way it still did it.

Thank you; any help is appreciated.

---

### Post by hanman on 2006-12-18
Well, my problem fixed itself, it seems.  I followed a sticky in this forum to use the latest nvidia drivers from this repository:

[http://www.albertomilone.com/drivers/edgy/nonlegacy/32bit](http://www.albertomilone.com/drivers/edgy/nonlegacy/32bit) binary/

it installed a new kernel along with the nvidia drivers, and after a reboot, everything was fine.  i still  don't know what the original problem was, but that's academic now.

thanks anyway, and sorry for wasting your time.

---

