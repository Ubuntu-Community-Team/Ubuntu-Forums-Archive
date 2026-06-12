---
title: "Onboard Sound Woes! Help!"
date: 2005-11-25
forum: Multimedia &amp; Video
---

### Post by MM23 on 2005-11-25
Alright-- here's my story.

I recently upgraded my old machine to a new one, and decided I didn't need my old 5.1 card (which worked perfectly with Ubuntu, by the by) because my new motherboard had built in 7.1 sound support. Well, that was a damn mistake, because although I have perfect working sound, NOTHING can share /dev/dsp. If one thing is using /dev/dsp (doesn't matter if it's using OSS, alsa, arts, whatever) nothing else can use it. This is annoying, since then I can't, say, listen to music in XMMS and watch a flash video with sound at the same time.

All the modules ALSA has loaded:


snd_intel8x0 30144 2 - Live 0xf8acd000
snd_ac97_codec 72188 1 snd_intel8x0, Live 0xf8d69000
snd_pcm_oss 46368 0 - Live 0xf8d5c000
snd_mixer_oss 16128 1 snd_pcm_oss, Live 0xf8a59000
snd_pcm 78344 4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss, Live 0xf8ada000
snd_timer 21764 1 snd_pcm, Live 0xf8aad000
snd 48644 9 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer, Live 0xf8ab5000
soundcore 9184 1 snd, Live 0xf8aa1000
snd_page_alloc 10120 2 snd_intel8x0,snd_pcm, Live 0xf8a26000


My motherboard is a Gigabyte nForce4 SLI board.

I have tried following the guide at [http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063) to no avail.

Someone help me, please. :(

---

### Post by Teroedni on 2005-11-26
you got no error using that howto?

you also checked every  channel and set it right using?
```
sudo alsamixer
``` 


Maybe you should try nforce corp drivers from nvidia
[http://www.nvidia.com/object/linux_nforce_1.0-0310.html](http://www.nvidia.com/object/linux_nforce_1.0-0310.html)

---

