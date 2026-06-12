---
title: "No Sound After Upgrade To Dapper."
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by Rzulf on 2006-06-08
I have a strange problem that when alsa works the oss doesn't and backwards. Moreover, I never know which one will work after a reboot. I have two cards and they are both detected.

---

### Post by oliwally on 2006-06-08
I have a similar problem. My computer has two sound cards - one onboard (via8235) and one card (SB live). I only ever want to use the SB live one but how do I make it the default? It seems that after playing around a bit with sound settings and then starting a new session I have sound, but after a reboot the sound is gone again. How do I load fix it so I consistently have sound? Is there perhaps a line that needs to be added to /etc/modprobe.d/alsa-base or somewhere like that?

---

### Post by lavinog on 2006-06-08
What happens when you disable the onboard card using bios? (if you can)

---

### Post by oliwally on 2006-06-09
> What happens when you disable the onboard card using bios? (if you can)

Hmmm...I'll have a go at that - see if I can find the option.

---

### Post by Whity on 2006-06-09
[QUOTE=oliwally]I have a similar problem. My computer has two sound cards - one onboard (via8235) and one card (SB live). I only ever want to use the SB live one but how do I make it the default? It seems that after playing around a bit with sound settings and then starting a new session I have sound, but after a reboot the sound is gone again. How do I load fix it so I consistently have sound? Is there perhaps a line that needs to be added to /etc/modprobe.d/alsa-base or somewhere like that?[/QUOTE]

I am sitting on the same situation. SB Live card and a onboard card, and no sound after dapper. Worked fine in breezy.

In console I am getting:

> ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default

---

### Post by oliwally on 2006-06-09
[QUOTE=lavinog]What happens when you disable the onboard card using bios? (if you can)[/QUOTE]

It worked!!!!!

What excellent advice - couldn't have been more easy. I've rebooted twice now and the sound was there straight away. Thanks so much.

---

### Post by Rzulf on 2006-06-10
But I still have a problem and I don't want to disable anything because I need 2 sound cards. What information shuold I provide. Because sometimes both OSS and ALSA don't work.

---

### Post by oliwally on 2006-08-20
Ok it's been a while and for some reason I have the same problem again, although my on-board soundcard is still disabled in the bios.

Amarok plays mp3s without any trouble but the system sounds just don't work. Not a peep.

KMix tells me there are two sound devices: My 'SB Live (Unknown)' and 'SAA7134' (which is not my onboard soundcard!). It seems to default to the SAA7134 card and I cannot get the sound going. 

Alsa Mixer doesn't recognize the SB Live at all and just shows the SAA7134.

What's going on? How do I tell Kubuntu to use the SB Live as default and ignore everything else? Why has it suddenly come up with this new (SAA7134) sound device? 

Please help.

---

### Post by oliwally on 2006-08-21
> What's going on? How do I tell Kubuntu to use the SB Live as default and ignore everything else? Why has it suddenly come up with this new (SAA7134) sound device?

I have also noticed that sometimes dapper *does* default to the SB Live card, in which case sound works.

---

### Post by oliwally on 2006-08-22
Any ideas? :(

---

### Post by oliwally on 2006-08-23
Bump ;) 
> 
What's going on? How do I tell Kubuntu to use the SB Live as default and ignore everything else? Why has it suddenly come up with this new (SAA7134) sound device?

---

