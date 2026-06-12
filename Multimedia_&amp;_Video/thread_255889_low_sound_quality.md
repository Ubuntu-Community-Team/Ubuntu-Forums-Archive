---
title: "low sound quality"
date: 2006-09-12
forum: Multimedia &amp; Video
---

### Post by Heinali on 2006-09-12
Hello friends!
How do I improve overall quality of sound playback? There's a big difference between sound quality in WinXP (Winamp or Apollo) and Ububntu 6.06 64 (Xmms) on my Roland DS-7 monitors. The sound is 'dry', 'plastic' and 'unclear' in Ubuntu (well, maybe there are really no difference if you use something like 'creative inspire') I have Audigy PlatinumEx (digital output) and use ALSA (tried OSS, Jackd - no changes) I suppose that's everything about drivers?

---

### Post by zettberlin on 2006-09-12
> **Heinali said:**
> Hello friends!
How do I improve overall quality of sound playback? There's a big difference between sound quality in WinXP (Winamp or Apollo)
 and Ububntu 6.06 64 (Xmms) on my Roland DS-7 monitors.


To be perfectly honest: I do not believe, that there is a really *big* difference. 
The difference of the output on driver-level between Linux and Windows is null.

The only difference, that could occur between the two systems used as you describe it (compressed media, digital out) would be the output gain in the mixer and the codecs used to play the files. The latter is in fact different so it would be usefull, if you would test this with uncompressed Media (wav, flac, aiff etc)

---

### Post by Heinali on 2006-09-12
> **zettberlin said:**
> To be perfectly honest: I do not believe, that there is a really *big* difference. 
The difference of the output on driver-level between Linux and Windows is null.

The only difference, that could occur between the two systems used as you describe it (compressed media, digital out) would be the output gain in the mixer and the codecs used to play the files. The latter is in fact different so it would be usefull, if you would test this with uncompressed Media (wav, flac, aiff etc)

 Ok, but I've tested this with wav. I do hear the difference - it sounds like it was downsampled 22khz, like that... Maybe I should play with ALSA configuration or smth? Big thanks!

---

### Post by zettberlin on 2006-09-12
> **Heinali said:**
> like it was downsampled 22khz

This would be strange but not entirely impossible. Maybe you should try to check/change settings for your card with a mixerapplication. Usually alsamixer (runs within a terminal) shows the most options for your cards chipset, gamix is quite complete also.

Your card uses an emu10k1-chipset, this one is the first one that was perfectly supported on my Linuxbox some 6 years ago ;-)



[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy2+ZS+Platinum+Pro.&chip=emu10k2%2C+CA0151%2FP16V&module=emu10k1](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy2+ZS+Platinum+Pro.&chip=emu10k2%2C+CA0151%2FP16V&module=emu10k1)

---

### Post by Heinali on 2006-09-13
Thanks! Seems like everything ok now

---

### Post by dolson on 2006-09-13
This was the biggest complaint I had about the SoundBlaster Live! 5.1 and newer cards, with ALSA. OSS sounded great for me, but ALSA was tinny (that's how I described it anyhow).

Someone tipped me off to configuring it properly using alsamixer in a console, and I found some good settings that make it sound awesome. However, you don't get the EAX stuff like you do in Windows, obviously. Not a big deal anyhow.

I found that with the Live 5.1 I had to lower the PCM volume to about 50-60% so it didn't clip, enable the tone controls, and adjust accordingly, and I think a couple other minor changes. The same sort of thing goes for my Audigy2 card, but I think the volume levels are well adjusted there.

Anyhow, glad you got it working, just posted so anyone who finds the thread has some ideas of what to try.

---

### Post by Heinali on 2006-09-14
> **dolson said:**
> 
I found that with the Live 5.1 I had to lower the PCM volume to about 50-60% so it didn't clip, enable the tone controls, and adjust accordingly, and I think a couple other minor changes. The same sort of thing goes for my Audigy2 card, but I think the volume levels are well adjusted there.

Anyhow, glad you got it working, just posted so anyone who finds the thread has some ideas of what to try.

 Could you please post all the changes you did for the Audigy2? In my case it seems like everything was about volume levels... but still I'm looking for a linux mp3 codec which is as good as the one in Apollo player (WinXP) Thanks!

---

