---
title: "no audio, first time user"
date: 2009-01-21
forum: Multimedia Software
---

### Post by OniFactor on 2009-01-21
sorry if this is way to commonly asked, but, i tried following the walkthrough thing, and it didn't help..

Ubuntu 7.1
EVGA mobo with what appears to be surround sound onboard audio.. there are 6 audio jacks, grey black orange pink green blue, i have my powered speakers plugged into the green jack.

this is what aplay -l gives me

```
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
i made sure the alsa device was selected in the volume control, not the oss.. unmuted practically everything, and still nothing. i tried making sure it was all unmuted in the alsamixer, that didn't do anything, either. then i tried the sudo apt-get install alsa-oss as i thought maybe the conflict is because i'm trying to play MP3s and have pidgin going at the same time? i also made sure that my user came up with the grep 'audio' bit, as well. totally confused.. can anyone help please?

---

### Post by hal8000 on 2009-01-21
Lets gather some more info first. Post the output of:

lspci -v | grep audio


and also:


lsmod | grep snd


I also have a motherboard with builtin audio, in my case its the Intel ICH5 chipset.  The kernel module is snd_intel8x0 as shown below:

anc@orac:/usr/share/sounds$ lsmod | grep snd
snd_intel8x0           35356  4 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
--snip--


It may have not been probed correctly, or wrong module in use.
Once the results of the commands are up, it may only be a matter of rmmod and modprobe to get your sound working.

---

