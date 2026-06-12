---
title: "sound works with LiveCD but not after installation"
date: 2008-08-23
forum: Multimedia Software
---

### Post by zoubidoo on 2008-08-23
I have a machine which plays sounds when running the LiveCD (8.04.1 desktop), but won't in the installed version.  Something must be different but I can't find what.

Following the very useful advice from [here]("http://ubuntuforums.org/showthread.php?t=205449")

1.  aplay -l lists the sound cards as expected
2.  alsamixer settings appear to be fine
3.  starting aplay gives  "audio open error: Device or resource busy"
4.  starting pulseaudio gives "Error opening PCM device hw:0: Device or resource busy" (pulseaudio isn't already running)

Any suggestions would be much appreciated!
Z.

Details:

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
$ aplay /usr/share/sounds/generic.wav 
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
aplay: main:546: audio open error: Device or resource busy

```

```
$ pulseaudio 
ALSA lib conf.c:3952:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM surround71:0
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0"): initialization failed.
ALSA lib conf.c:3952:(snd_config_expand) Unknown parameters 0
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM surround71:0
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-source" (argument: "device_id=0 source_name=alsa_input.pci_8086_24d5_sound_card_0_alsa_capture_0"): initialization failed.

```

Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

---

### Post by wolfen69 on 2008-08-23
see [this]("https://help.ubuntu.com/community/HdaIntelSoundHowto") page. hope it helps.

---

### Post by zoubidoo on 2008-08-25
> **wolfen69 said:**
> see [this]("https://help.ubuntu.com/community/HdaIntelSoundHowto") page. hope it helps.

Thanks for the reply.  I've read through the page but can't see anything that appears relevant.  Of course I can rebuild alsa but if it's working on the livecd then it can't be that.

It seems that either alsa is refusing access because an existing application is accessing it (How can one tell which applications are currently accessing alsa) or it's a permission problem - ie for some reason my user is not allowed to access alsa.

Any pointers would be much appreciated,
Cheers,
Z.

---

