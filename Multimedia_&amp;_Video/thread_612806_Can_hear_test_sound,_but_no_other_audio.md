---
title: "Can hear test sound, but no other audio"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by sshorter on 2007-11-14
Hi all.  Running fresh install of 7.10, experienced linux user, but fairly inexperienced linux administrator.

My problem is that I can hear sound playback from the sound preferences panel's test button, but not any other way.

Here's some config info:

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

lspci -v
```
...
00:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at e100 [size=256]
        Capabilities: <access denied>
...
```

I can hear the test sound when I select one of the following:
[LIST][*]C-Media PCI IEC958
[*]C-Media PCI DAC/ADC
[/LIST]

However, even when the test sound plays, I cannot get sound any other way, including from selecting system sounds and clicking the play button, or by going to youtube, or whatnot.

Please advise!  Thanks in advance!

---

### Post by Yellow Pasque on 2007-11-14
It looks like you have two sound cards: VIA onboard audio and a CMI8738 based card, correct? If you can't find a solution, look into OSSv4 (in my signature). It supports both devices.

---

### Post by amadeov on 2007-12-08
> **sshorter said:**
> Hi all.  Running fresh install of 7.10, experienced linux user, but fairly inexperienced linux administrator.

My problem is that I can hear sound playback from the sound preferences panel's test button, but not any other way.

Here's some config info:

However, even when the test sound plays, I cannot get sound any other way, including from selecting system sounds and clicking the play button, or by going to youtube, or whatnot.

Please advise!  Thanks in advance!

I have this exact same problem and have the same card installed.  I have my VIA onboard audio turned off in my BIOS, though, so the only card that I have installed is the C-media PCI.  I have installed the ALSA drivers directly and I've also installed them through module assistant, with the same result.  I can hear test sounds (but only on the "2nd DAC"), but nothing else works for sound.  I will try the OSS method and report back, I guess.

---

### Post by amadeov on 2007-12-08
Okay, with OSS installed as per your instructions on the other post, I still have exactly the same problem.  I can hear the test sounds, but nothing else. =(  Any ideas?

---

