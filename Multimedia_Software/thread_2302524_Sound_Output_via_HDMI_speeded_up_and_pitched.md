---
title: "Sound Output via HDMI speeded up and pitched"
date: 2015-11-11
forum: Multimedia Software
---

### Post by tim138 on 2015-11-11
Hi everyone,
after fixing some issues of getting HDMI sound work at all on my MSI GP70 notebook running Ubuntu 14.04, I am facing another issue and hope you can help me out with that.

When switching the sound output to "HDMI/DisplayPort 3", my externally connected monitor plays the required sounds, but they are pitched (higher than they are when I choose the built-in speaker of the notebook) and seem to be played faster. My first guess would be an issue with the sampling rate, but I am absolutely not sure what to try next and am afraid of screwing everything up ;-). I've already tried upgrading ALSA as described in [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS), but this makes the situation even worse, resulting in no audio played back at all via HDMI.

Here are some outputs related to my system:

cat /proc/asound/cards

```
 0 [HDMI           ]: HDA-Intel - HDA Intel HDMI
                      HDA Intel HDMI at 0xf7b14000 irq 53
 1 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7b10000 irq 54

```

aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


head -n 1 /proc/asound/card0/codec*

```
Codec: Intel Haswell HDMI
```


Thanks for your support! Let me know if you need additional information.

Tim

---

### Post by tim138 on 2015-11-13
After a lot of research, I've finally found out the solution.

According to [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1288004](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1288004), I set the following Kernel parameter:

```
i915.disable_power_well=0
```

And the sound works perfectly :)

---

