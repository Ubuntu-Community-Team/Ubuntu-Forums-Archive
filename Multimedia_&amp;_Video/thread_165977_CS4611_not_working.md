---
title: "CS4611 not working"
date: 2006-04-25
forum: Multimedia &amp; Video
---

### Post by ActionMutant on 2006-04-25
I can't seem to get my soundcard working. I've had it working on other versions of Linux but just installed Ubuntu for the first time and can't figure out what the issue is.

The computer is a Dell R350, not a Thinkpad so I know it's not a misidentified CS4232. I even looked at the motherboard, the chip itself says CS4611.

Here are the few things I've done:
```
:~$ sudo modprobe snd-card-cs461x
Password:
FATAL: Module snd_card_cs461x not found.
```

```
:~$ lsmod|grep cs46
snd_cs46xx             78664  0
gameport               14472  3 ns558,snd_cs46xx
snd_rawmidi            22816  1 snd_cs46xx
snd_ac97_codec         72188  1 snd_cs46xx
snd_pcm                78344  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd                    48644  8 snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         10120  2 snd_cs46xx,snd_pcm
```

```
:~$ cat /proc/asound/cards
--- no soundcards ---
```

I don't know where to go from here. Any help would be appreciated.

---

