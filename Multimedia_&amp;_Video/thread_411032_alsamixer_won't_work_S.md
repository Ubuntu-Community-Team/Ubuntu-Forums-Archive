---
title: "alsamixer won't work :S"
date: 2007-04-16
forum: Multimedia &amp; Video
---

### Post by Mr_Sun on 2007-04-16
I have some strange sound problems... 
First of all, when I try to load alsamixer in the treminal, it wont work. 
This is the output:

alsamixer: function snd_mixer_load failed: Invalid argument


Another strange problem is, whenever I restart my laptop, I only get sound on the right channel :S
But if I i mute and unmute in the volume control, I get sound on both channels. But it's pretty irritating to do this every time, so how can I fix these two problems?

Thanks in advance :)

---

### Post by Mr_Sun on 2007-04-17
bump

---

### Post by Jessard on 2007-05-30
Same problem here (Acer Apsire 5100 with "ATI Technologies Inc SB450 HDA Audio"). I see this splattered all over the internet, but no good solutions so far. At the very least I think it would work to use something like aumix (as opposed to amixer / alsamixer, which of course we can't use) on startup to automatically fiddle with the settings (mute/unmute ?) and hopefully fix it. Kludgy, but might work. I'll try it after a reboot. :|

. . .

Hmm, that seems to get it going! Of course, it's still technically broken, but at least now it's out of the way. I added
```

aumix -v0
aumix -v60
```
To a script that runs at the end of my current runlevel. No idea *why* it works, but hey, I won't argue...

---

### Post by vultaire on 2007-06-05
Same exact issue.  Just bought this laptop two days ago, Acer Aspire 3103WLMi - yes, another Acer with the same issue.  Sound card is identical according to lspci, however gnome volume control lists it as a "Realtek ALC883" (OSS Mixer).

Thanks for the tip on muting/unmuting; that works here too.  Now I'm very happily using a fast Ubuntu installation instead of the slow-as-molasses Windows Vista which was preinstalled.

---

