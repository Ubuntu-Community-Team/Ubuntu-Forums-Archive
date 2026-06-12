---
title: "No sound on Toshiba Qosmio F50, Ubuntu 8.10"
date: 2009-04-05
forum: Multimedia Software
---

### Post by dougbe on 2009-04-05
Hi Folks,

I've just installed Ubuntu 8.10 on my Toshiba Qosmio F50 and despite several hours of googling and reading forum posts I can't get the sound to work. Here's the basic info:

Toshiba Qosmio F50
Ubuntu 8.10
Realtek AL C272-GR Soundcard

I've read posts about using pulse audio, and others about setting everything to ALSA, neither approach has worked for me thus far. To be clear, I get no sound at all, ever, not even the little drum sound that plays when the login screen for Ubuntu appears. I'm dual-booting with Vista and the sound works fine in Windows, so I know it's not a hardware problem. And volume levels are full everywhere I look, with nothing muted.

Finally, one post suggested I run the command:

```
aplay -l
```

To see if my sound card was detected. The output was:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC272 Digital [ALC272 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Which I assume to mean that linux is recognizing the sound card.

Any help would be very much appreciated.

---

### Post by bertolo on 2009-04-05
try this:
open volume control, preferences, enable all the xit there. put volume in max in all parameters.
then in switches choose headphones and disable the other two options below.
ps:select HDA intel drivers.
this was my solution when i had the same problem

---

### Post by dougbe on 2009-04-06
That did the trick! Sir, you are a life saver.

Many thanks :-)

---

### Post by bertolo on 2009-04-06
ahahhaha :) no prob.
sometimes the best solution is the easy one.
you are welcome

---

### Post by markackerman8@gmail.com on 2009-11-01
Hey Guys I am having real problems with sound too after a clean install of karmic and with grug2. ARghhhhhh I have looked everywhere and tried all the troubleshooting guides with no success double arghhhhh

Everything that points to an output device only shows the"dummy" (WITH PADEVICECHOOSER or system/preferences/sound_preferences),

but when I:

ack@Titan:~$ gnome-alsamixer ... it shows "Realtec ALC268"

or
ack@Titan:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
Subdevices: 0/1
Subdevice #0: subdevic

or
ack@Titan:~$ lspci -v
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
Subsystem: Hewlett-Packard Company Device 30cc
Flags: bus master, fast devsel, latency 0, IRQ 22
Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

ANY SUGGESTIONS?????

---

