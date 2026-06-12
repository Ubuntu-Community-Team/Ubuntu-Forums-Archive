---
title: "No sound after Upgrade"
date: 2009-11-19
forum: Multimedia Software
---

### Post by whinis on 2009-11-19
I recently upgraded my 9.04 jaunty to 9.10 karmic. I had graphics problems so I reinstalled using cd and the proprietary drivers started to work again however now i have no sound

I am using a m3a78-t asus mobo dual core 3.0 amd and ati radeon 4870

here is I have tried 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) ( installed drivers for my alc1200 but didn't activate it )
[http://ubuntuforums.org/showthread.php?t=1316634](http://ubuntuforums.org/showthread.php?t=1316634) ( as far as i can tell all it did was delete my /proc/asound/ folder)

results from terminal
```
aplay -l
aplay: device_list:223: no soundcards found..

lspci -v
*cliped*
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
    Subsystem: Hightech Information System Ltd. Device aa30
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at fe9ec000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
*clipped

alsamixer
alsamixer: relocation error: alsamixer: symbol snd_mixer_selem_is_enum_capture, version ALSA_0.9 not defined in file libasound.so.2 with link time reference


```after recompiling the hda-intel ( which seems to be missing from main install/upgrade) I get
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by Ulysses361 on 2009-11-20
Please send us output from step 3 and step 4 from this procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Please also specify the exact model and make of pc that you are using (if possible)

---

