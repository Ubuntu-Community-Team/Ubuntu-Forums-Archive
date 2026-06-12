---
title: "Sound works on boot, but after left for x amount of time it stops?"
date: 2009-03-18
forum: Multimedia Software
---

### Post by mortuk on 2009-03-18
Ok so when I boot / reboot my sound is working fine. Yet after I leave it for a while and come back to it (ie over night) I got nothing and have to reboot to get sound, which isnt always convenient as this is my work machine.

I have tried a few things on the sound problem sticky, as well as 'sudo /etc/init.d/alsa-utils restart' and nothing seems to want to work, any ideas?

I dont think its a driver issue as obviously its working until something happens to stop it working, but I have no idea what :( Hopefully below will be some useful info.

Output of 'aplay -l'
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC885 Analog [ALC885 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC885 Digital [ALC885 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Audio section of 'lspci -v'
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fa100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

---

### Post by mortuk on 2009-03-20
anyone?

---

### Post by change_mode on 2009-03-20
Does it go to suspend/hibernate mode when you leave it for so long? Suspend and hibernate can cause trouble.

Check Preferences > Screensaver > Power Management

---

### Post by Anthon on 2009-03-20
Which version of Ubuntu are you on? I had problems with 8.04: after viewing thing on youtube the sound would not work anymore for rythmbox or skype. However this problem has gone with 8.10.
But you seem to indicate this happens without you running any programs after rebooting. Is that correct?

Have you grepped /var/log/messages for 'audio'

---

