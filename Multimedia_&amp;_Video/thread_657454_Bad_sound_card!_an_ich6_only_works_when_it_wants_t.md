---
title: "Bad sound card! an ich6 only works when it wants to."
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by Leso on 2008-01-03
Hi guys. I've been trying to fix the laptop of a cousin (he moved from win se to ubuntu 6.10), and everything works better... but the sound. At first it worked allright, the startup sound and the logout sound were heard very loudly. But, then Rythmbox and totem froze to death when trying to play any sound, When i tried to play the system sounds in gnome-sound-properties, it also froze. The laptop is an olidata 223ei0 and *lspci | grep -i audio* gives me this;

[COLOR="DarkSlateGray"]**mnpena@mnpena-laptop:~$ lspci | grep -i audio**
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)


**mnpena@mnpena-laptop:~$ asoundconf list**
Names of available sound cards:
ICH6

**mnpena@mnpena-laptop:~$ cat /proc/asound/cards**
 0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with VIA1612A at irq 21




**mnpena@mnpena-laptop:~$  lsmod | grep -i snd**
snd_atiixp_modem       17160  0 
snd_via82xx_modem      16264  0 
snd_intel8x0m          18572  0 
snd_intel8x0           34972  7 
snd_ac97_codec        100644  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  9 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  5 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  21 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm
[/COLOR]

 It's driving me nuts! I already tried reinstalling alsa, disabling the esd and whatnot.

---

### Post by Leso on 2008-01-21
Fixed it. Just disabled the propietary drivers for the modem and everything worked allright.
I forgot to post the solution here XD

---

### Post by tgalati4 on 2008-01-21
Perhaps the modem and the sound card share the same interrupt.  Check them with:

>cat /proc/interrupts

---

