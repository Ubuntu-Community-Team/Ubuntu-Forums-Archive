---
title: "no microphone"
date: 2006-09-30
forum: Multimedia &amp; Video
---

### Post by areks on 2006-09-30
Hi,

I have problem with recording sound from any program. I believe this could be because my sound configuration is wrong or maybe something is missing.

After browsing other post with similar problems I found 2 strange things in my system:
1) in alsamixer I have only: Maser, PCM, Capture - no Mic, Microphone or anything similar. 
2) my /etc/esound/esd.conf is empty

In one of posts I found aadebug script. Here is the output:
```

ALSA Audio Debug v0.1.0 - sob wrz 30 23:12:41 CEST 2006
http://alsa.opensrc.org/index.php?page=aadebug
http://www.gnu.org/licenses/gpl.txt

Kernel ----------------------------------------------------
Linux malamocco 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_hda_intel          20468  4
snd_hda_codec         166096  1 snd_hda_intel
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26884  2 snd_pcm
snd                    60004  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         11304  2 snd_hda_intel,snd_pcm

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).
0 [Intel          ]: HDA-Intel - HDA Intel
                     HDA Intel at 0xde300000 irq 66
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
 33:       : timer
cat: /proc/asound/hwdep: File not found
00-00: HDA Generic : HDA Generic : playback 1 : capture 1
cat: /proc/asound/seq/clients: File not found

Dev Snd ---------------------------------------------------
controlC0  pcmC0D0c  pcmC0D0p  timer

CPU -------------------------------------------------------
model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz
cpu MHz         : 1663.480
model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz
cpu MHz         : 1663.480

RAM -------------------------------------------------------
MemTotal:      2072584 kB
SwapTotal:     2104504 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)

```

Again it looks some configuration files are missing. 
Does anyone knows how I could fix it, or maybe reinstall sound card drivers (or something like this).

On same laptop running under WinXP there is no problem with recording sound with internal or external microphone.

Thanks for any help
Arek

---

### Post by ryu kun on 2006-09-30
Same CPU, same sound card, very similiar problem: there is a mic in my mixer but it's disabled, and I couldn't find how to enable or how to make it work. 

From my searches I've got the opinion that microphone problem is widely known but there is currently no solution, so everyone stays in silence.

Good luck.

---

