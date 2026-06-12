---
title: "Microphone not in Alsamixer"
date: 2006-09-10
forum: Multimedia &amp; Video
---

### Post by teb on 2006-09-10
My Dapper installation on the Vaio SZ28 is working great. Sound works, but only can I still not enjoy the microphone: neither the internal nor the external mike don't show up in Alsamixer. Only two channels are seen: Master and PCM. It uses the HDA Intel driver; the device selected is HDA Intel (Alsa mixer).

lspci | grep Audio gives me:
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

I have no idea how to enable the mike. It is in the Devices Manager I can see a "HDA Generic ALSA Capture Device" listed.  

I hope anyone can point me in the right direction.

cheers,

Wouter

---

### Post by teb on 2006-09-15
So when I run alsamixer, there are two playback channels, being PCM and Master and in the Capture view it is empty. How do we get the capture device activated here?

In otherwords, the output of amixer:
amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 70 [55%] [on]
  Front Right: Playback 83 [65%] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%]
  Front Right: Playback 255 [100%]


More details:
1) aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

2) lspci -v
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Sony Corporation: Unknown device 81e6
        Flags: bus master, fast devsel, latency 0, IRQ 74
        Memory at dc340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

3) lsmod | grep snd
snd_hda_intel          20468  6
snd_hda_codec         163088  1 snd_hda_intel
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26884  2 snd_pcm
snd                    60004  16 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_hda_intel,snd_pcm

4)  cat /proc/asound/cards
0 [Intel          ]: HDA-Intel - HDA Intel
                     HDA Intel at 0xdc340000 irq 74


5) cat /proc/asound/pcm
00-00: HDA Generic : HDA Generic : playback 1 : capture 1

6) arecord --list-devices
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Anyone?

---

### Post by mexlinux on 2006-09-20
Same problem
Has anyone a solution for this?

---

### Post by mexlinux on 2006-10-30
Since edgy 6.10 comes with an old ALSA, this problem is still present

---

### Post by ulefr01 on 2006-11-27
Solution ?

---

### Post by mexlinux on 2006-11-27
In edgy I have compilaed latest alsa driver (very easy), and it's working!

---

