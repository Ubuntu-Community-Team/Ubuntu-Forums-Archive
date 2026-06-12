---
title: "sound available only when moving master volume slides"
date: 2006-07-08
forum: Multimedia &amp; Video
---

### Post by veli on 2006-07-08
Generally, the sound initially worked on my Dapper. If booting from the Live CD, the sound works. After the HDD installation was OK, but after updating the system and after reboot the sound is not working (one can barely hear the log in sound in the background, very weak). All volumes are unmuted. When moving the Master volume slides, the sound appears and it's working untill the next reboot. After log in-log out, the sound is OK. 

I tried sudo alsactl store 0, no luck. The levels are stored, but I still have to move the master volume.

I reinstalled the alsa package via Synaptic, same result.

The sound card is ESS Allegro PCI.

I'd appreciate any ideas, thanks

---

### Post by veli on 2006-07-09
OK, I tried everything but the problem persists. Now, what about reloading the drivers again? 

I'd appreaciate any comments and guidence to preconfigure the sound card again. I hope it'll fix the problem. Thanks

---

### Post by veli on 2006-07-12
I'm still looking for solution of the problem with sound on 6.06. I change the sound servers, sometimes the sound appeares, sometimes no, independently on the sound system. Sometimes only the right channel is switched on. I did the aadebug script and here is the result. I have no idea about the results, and I'll be happy to get those results explained. Look at the text in red. Thanks a lot.

 2.6.15-26-686 #1 SMP PREEMPT Fri Jul 7 19:48:22 UTC 2006 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_maestro3           27780  4
snd_ac97_codec        100224  1 snd_maestro3
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  5 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd_page_alloc         11304  1 snd_pcm
snd                    60004  12 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer

[COLOR="Blue"][COLOR="Red"]Modprobe Conf ---------------------------------------------
Warning: module config file does not exist[/COLOR][/COLOR]
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).
0 [PCI            ]: Allegro - ESS Allegro PCI
                     ESS Allegro PCI at 0x7800, irq 9
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
 33:       : timer
cat: /proc/asound/hwdep: No such file or directory
00-00: Allegro : Allegro : playback 2 : capture 1
cat: /proc/asound/seq/clients: No such file or directory

Dev Snd ---------------------------------------------------
controlC0  pcmC0D0c  pcmC0D0p  timer

CPU -------------------------------------------------------
model name      : Pentium III (Coppermine)
cpu MHz         : 662.353

RAM -------------------------------------------------------
MemTotal:       255520 kB
SwapTotal:      522072 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
0000:00:02.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 20)
0000:00:12.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 10)

---

### Post by BuffaloX on 2006-07-12
I have something somilar, No sound in left channel until i nudge the volume.
I guess my right channel is muted.
Havn't found a way to fix it yet.

---

### Post by BuffaloX on 2006-07-12
At last I fugured mine out.

It turned ou to be very simple, I hope yours is too.
I simply had to switch deamphasis off, turned out it was on for right, and off for left channel.

I found this setting in Volume control / options.
There is also a bunch of other options.

---

### Post by alexamike on 2006-07-16
Well, I have same problem, but alas, the option quoted above doesn't exist on my volume control ... what's up?

---

### Post by encompass on 2006-08-22
I couldn't find that volume setting in alsamixer... but I do have the sound card problem you have
0000:00:08.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
from lspci

---

### Post by encompass on 2006-08-24
Moi Veli!
The sound issue that you discribe is a bug in the driver... they are working on it now.  I checked on the alsa website.
(I also reported  a few bugs myself while I was there) ¶:

---

