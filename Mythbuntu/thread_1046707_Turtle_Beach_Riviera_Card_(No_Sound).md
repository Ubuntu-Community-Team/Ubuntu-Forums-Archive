---
title: "Turtle Beach Riviera Card (No Sound)"
date: 2009-01-21
forum: Mythbuntu
---

### Post by jr_herman on 2009-01-21
Hello I've installed mythbuntu. My onboard audio works fine. However I do have a turtle beach sound card that my computer recognizes but wont play sound through it. I could really use some help in getting this issue resolved. Thanks in advance.

I used this command in the terminal```
aplay -l
``` Here is what i received back.
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0 Then I run ```
lspci -v
```

Then I received...
> 04:00.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: C-Media Electronics Inc CM8738
	Flags: bus master, stepping, medium devsel, latency 32, IRQ 20
	I/O ports at d000 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: C-Media PCI
	Kernel modules: snd-cmipci

Then...cat ```
/proc/asound/cards
``` Gave me this...
> 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xe5200000 irq 16
 1 [CMI8738        ]: CMI8738-MC6 - C-Media CMI8738
                      C-Media CMI8738 (model 55) at 0xd000, irq 20

-Could it be as simple as disabling the onboard sound?

I'm really a bit lost. Please Help

---

### Post by jr_herman on 2009-01-28
Sorry for the duplicate post. Here is the solution here.
[http://ubuntuforums.org/showthread.php?t=1046715]("http://ubuntuforums.org/showthread.php?t=1046715")

---

