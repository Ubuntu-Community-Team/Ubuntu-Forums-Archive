---
title: "Horrid sound out of wrong Sound Output device"
date: 2008-07-28
forum: Multimedia Software
---

### Post by sputnikkk on 2008-07-28
aplay -l result ins this ....

> cierra@cc-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SBLive! Value [CT4832]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Live [SBLive! Value [CT4832]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SBLive! Value [CT4832]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Speakerphone [Logitech EasyCall Speakerphone], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Sound comes out of the USB speakerphone thing but NOT the sound card...  How can I get this to work right?

Ubuntu newb ,,,

---

### Post by Yellow Pasque on 2008-07-28
Go to the terminal and run the following: (I'm not sure if it needs root permissions, and I don't have ALSA, so I can't test it. If it does, put sudo in front of the command).
```
asoundconf
```

---

### Post by sputnikkk on 2008-07-28
thank you ...

> cierra@cc-desktop:~$ asoundconf
Usage:
asoundconf is-active
asoundconf get|delete PARAMETER
asoundconf set PARAMETER VALUE
asoundconf list

Convenience macro functions:
asoundconf set-default-card PARAMETER
asoundconf reset-default-card
asoundconf set-pulseaudio
asoundconf unset-pulseaudio


List tells me this ...

> 
cierra@cc-desktop:~$ asoundconf list
Names of available sound cards:
Live
Speakerphone


not quite sure what to do with this info

---

### Post by cariboo on 2008-07-29
Double click the speaker icon in the top panel when the Volume control panel opens up and select your device.

Jim

---

### Post by sputnikkk on 2008-07-29
Thanks cariboo and all of you - but still no joy.  

Test tones all still emit from the USB - and thats all the sounds Im getting out of this system!

next idea?

---

### Post by Yellow Pasque on 2008-07-29
```
asoundconf set-default-card Live
```

---

### Post by sputnikkk on 2008-07-30
Did that .... changed the speaker setup to a know working speaker system and viola.

Speakers were the culprit

---

