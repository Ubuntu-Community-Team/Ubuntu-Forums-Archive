---
title: "No Sound Output"
date: 2007-05-12
forum: Multimedia &amp; Video
---

### Post by IntuitiveNipple on 2007-05-12
I'm having weird results trying to get sound to play-back on Edgy and/or Feisty installed on an Asus A7N266-VM motherboard. After hacking about for hours I'm hoping someone else might have a flash of inspiration to help solve this!

The motherboard has the integrated nvideo nforce2 chipset with the Realtec ALC650E sound system. The sound devices all appear to be detected correctly for/by ALSA and the mixers operate the controls.

Which-ever version of Ubuntu is installed, the standard 2-channel audio output just doesn't work.

It has the 'standard' three 3.5mm stereo jack sockets with lime=line out, blue=line in, and pink=microphone.

With ALSA configured with "Channel Mode" "2ch" it will record from the microphone and from line-in, but will not playback on line-out (although sounds are being played, as shown by Audacity's output monitor).

With ALSA configured with "Channel Mode" "4ch", and "Duplicate Front", sound is heard properly coming from line-in, but not from line-out.

With ALSA configured with "Channel Mode" "4ch" and no "Duplicate Front", there is no sound from either line-in or line-out!

All tests were done using speaker-test -c 2 or -c 4.

I've tried everything I can think of but can't get sound from line-out! The results below were generated from Edgy (6.10) but it's the same with Feisty too.
```
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.12rc1 (Thu Jun 22 13:55:50 2006 UTC).

$ cat /proc/asound/cards
 0 [nForce         ]: NFORCE - NVidia nForce
                      NVidia nForce with ALC650E at 0xed000000, irq 193

$ cat /proc/asound/devices
  2:        : timer
  3: [ 0- 2]: digital audio playback
  4: [ 0- 1]: digital audio capture
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0]   : control
$ cat /proc/asound/oss-devices
cat: /proc/asound/oss-devices: No such file or directory

$ cat /proc/asound/timers
G0: system timer : 4000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
P0-1-1: PCM capture 0-1-1 : SLAVE
P0-2-0: PCM playback 0-2-0 : SLAVE

$ cat /proc/asound/pcm
00-02: Intel ICH - IEC958 : NVidia nForce - IEC958 : playback 1
00-01: Intel ICH - MIC ADC : NVidia nForce - MIC ADC : capture 1
00-00: Intel ICH : NVidia nForce : playback 1 : capture 1

$ sudo lsmod | grep snd
snd_intel8x0           33436  4 
snd_ac97_codec         96672  1 snd_intel8x0
snd_ac97_bus            2432  1 snd_ac97_codec
snd_pcm_oss            46080  0 
snd_mixer_oss          18560  2 snd_pcm_oss
snd_pcm                80520  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd                    55428  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9952  2 snd
snd_page_alloc         10504  2 snd_intel8x0,snd_pcm

$ uname -a
Linux tom 2.6.17-10-386 #2 Tue Dec 5 22:26:18 UTC 2006 i686 GNU/Linux

```

---

### Post by IntuitiveNipple on 2007-05-13
Finally solved this, and thankfully it had nothing to do with the software at all. It was a combination of hardware configuration, undocumented motherboard jumpers in the manual, and operator error :oops: 

The easiest part was discovering that on the 2nd system I'd forgotten to turn on the speaker amplifier! As soon as I did that sound was alive and well.

I had read and re-read the motherboard manual in case there was a jumper to configure sound output. I saw a forum post talking about the A8V motherboard having to be jumpered to send audio to the rear ports. I checked the A7B266-VM manual but there was no indication in pictures or words. See the 1st attached image (A7N266-VM.jpg).

Later I found a throw-away mention by someone else that this motherboard requires jumpers to feed sound to the rear line-out socket, so I decided to open up both the PCs here and compare. Sure enough, the working motherboard has two jumpers on the AAPANEL connector!

So it seems these Asus A7N266-VM motherboards have a combined connector/selector (AAPANEL)  to feed the audio signals to a panel on the front of the case or to the rear line-out socket.

To use the rear line-out socket you must jumper the line-out left and line-out right pins of AAPANEL. Looking at the motherboard from the front, they are the first & third pairs.

The 2nd attachment is a photograph BEFORE the jumpers are in place, and the 3rd shows the jumpers fitted.

---

