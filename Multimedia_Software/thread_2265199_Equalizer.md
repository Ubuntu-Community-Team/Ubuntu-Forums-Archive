---
title: "Equalizer"
date: 2015-02-13
forum: Multimedia Software
---

### Post by cl-netbox on 2015-02-13
To improve the sound quality [COLOR=#000000]of my notebook[/COLOR] I tried:

equalizer plugin for ALSA (LADSPA-plugin)
qpaeq (freedesktop-pusleaudio / webupd8)
rhythmbox-plugin-equalizer (fossfreedom)

None of the online published solutions worked.
Does anybody have an idea for a workaround?

My current system is ubuntu 14.10 amd64 version.
These are the specifications of my sound devices:

 0 [HDMI           ]: HDA-Intel - HDA Intel HDMI
                      HDA Intel HDMI at 0xf7a14000 irq 48
Codec: Intel Haswell HDMI

 1 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7a10000 irq 49
Codec: VIA VT1802

card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: VT1802 Analog [VT1802 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: VT1802 Digital [VT1802 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 2: VT1802 Alt Analog [VT1802 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Yellow Pasque on 2015-02-14
Do you mean that the equalizers did not function correctly/at all, or do you mean that they didn't improve your sound no matter what equalizer settings you used?

For qpaeq, some tips here may help: [https://wiki.archlinux.org/index.php/PulseAudio#Equalizer](https://wiki.archlinux.org/index.php/PulseAudio#Equalizer)

---

### Post by cl-netbox on 2015-02-14
Sorry for not being clear enough, this is one solution I already had tried.
Equalizer was loaded after reboot and choosable from sound settings.
But qpaeg did not launch, so I could not change the frequencies.
LADSPA plugin launched, but the changes I made had no impact.

Thanks for your reply anyway - maybe you have another clue?

---

### Post by Yellow Pasque on 2015-02-14
So when you launched qpaeq from the terminal, what did it say?

Also, waht happened with rbox eq?

---

### Post by cl-netbox on 2015-02-14
When I try to launch qpaeq from terminal nothing happens - it does not launch.

---

