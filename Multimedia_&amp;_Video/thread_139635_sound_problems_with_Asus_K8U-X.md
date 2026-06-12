---
title: "sound problems with Asus K8U-X"
date: 2006-03-04
forum: Multimedia &amp; Video
---

### Post by peppy on 2006-03-04
I have an AMD64 system on an Asus K8U-X motherboard. However, I
haven't had success using ALSA and I have no sound at the moment.

The sound card is identified this way:

# lspci | grep audio
0000:00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI
AC-Link Controller Audio Device (rev 20)

alsaconf, however, properly identifies that this card should use the
snd-intel8x0 module. A look at the Sound Card Matrix at the ALSA page
shows that this module is indeed the one for this card.

However, when the module is loaded, these messages are printed:

ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 18 (level, low) -> IRQ 22
AC'97 0 does not respond - RESET
ACPI: PCI interrupt for device 0000:00:04.0 disabled
Intel PCH: probe of 0000:00:04.0 failed with error -13

The module does load, as you can see:

# lsmod | grep snd
snd_intel8x0           34216  0
snd_ac97_codec        101244  1 snd_intel8x0
snd_ac97_bus            2880  1 snd_ac97_codec
snd_pcm_oss            51424  0
snd_mixer_oss          17472  1 snd_pcm_oss
snd_pcm                90252  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24008  1 snd_pcm
snd                    57984  6
snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10720  1 snd
snd_page_alloc         11344  2 snd_intel8x0,snd_pcm

But not soundcards are identified:

# cat /proc/asound/cards
--- no soundcards ---

And running alsamixer produces

# alsamixer
alsamixer: function snd_ctl_open failed for default: No such device

kernel is:
2.6.15-17-amd64-generic #1 SMP PREEMPT Fri Mar 3 00:47:52 UTC 2006 x86_64 GNU/Linux

Does anybody have any hints?

---

### Post by marciovinicius on 2006-05-25
I have exactely the same problem (everybody who tries to use Ubuntu64 with AsusK8U-X have this problem) and I found some hope [here]("http://www.ubuntuforums.org/showthread.php?p=817147#post817147"). But unfourtunately I didn't understand...<img>

---

