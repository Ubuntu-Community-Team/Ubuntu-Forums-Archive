---
title: "Laptop microphone regression in Jaunty"
date: 2009-05-02
forum: Multimedia Software
---

### Post by minj on 2009-05-02
I have a problem with my integrated microphone. I was using it with no problems in Hardy but after installing Jaunty it behaves in very weird way.

Here's some info:
I have an Asus Z37S laptop.
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

$ cat ~/.pulse/*default*
alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0
alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0
```

Pulseaudio is selected everywhere in Sound preferences...

Anyway, when I plug in a headset with a microphone, everything is fine. "Capture" slider in Recording tab adjusts recording volume and "Front Mic"+"Front Mic boost" in Playback tab controls microphone sound output to the speakers.

However, when I plug it off and use my integrated microphone, the following happens:

"Front Mic"+"Front Mic boost" in Playback tab still works fine, I can hear mic's sound in the speakers.

BUT I cannot record anything! All I hear is static, no matter the
"Capture" slider in Recording tab.

And the weird part: if set both "Front Mic"+"Front Mic boost" to max and record some sounds I can hear an extremely faint sound in right channel of the recording.

I tried it on Jaunty livecd and experienced the same behaviour. Intrepid livecd works fine though. Something must have happened between those two :/

I do not know if that's relevant but I am suffering this bug as well [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201957](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201957) (using the workaround with "Surround" channel)

If you think some other information is relevant I can provide it just give me the commands :)

Please help, I coped with all the short-comings of Jaunty so far and don't really want to downgrade to Intrepid but I will be forced to do so since I don't like external microphones (I borrowed this one)

---

### Post by minj on 2009-05-06
anyone?

---

### Post by minj on 2009-05-07
=) I was messing around with volume control and it stroke me that input source is set to Mic. Changing it to Front Mic solves the problem.

Epiphany, heh?

---

