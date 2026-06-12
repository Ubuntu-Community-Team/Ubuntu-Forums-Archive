---
title: "On-board sound problems"
date: 2006-08-12
forum: Multimedia &amp; Video
---

### Post by GlennB on 2006-08-12
Hi All,

I'm having trouble disabling my on-board sound. I followed a bunch of suggestions in posts here, but have only managed intermittent success. The system has on-board sound from a SiS chipset, which works, but I also have a SB-Live value that I would prefer to use.

There are no bios options or jumpers (that I can find) to disable the Sis audio system.

To get the SB as the default, I edited the /etc/modprobe.d/alsa-base file so that the cards were enumerated like this:

```
options snd_emu10k1 index=0
options snd_intel8x0m index=1
```

When I first did this, and rebooted, the SB live card worked fine. However, following the next reboot, things had gone wrong! If I do:

```
aplay -l
``` 

I get this:

```
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

No mention of the SB card at all.

```
lsmod | grep snd
``` 

shows that the snd_emu10k1 module (for the SB Live) is loaded, but the alsa mixer doesn't see it, it doesn't appear on the device list.

Help! What did I do? All I need is a way to disable the SiS audio device, and use the SB as the default.

Thanks,

Glenn.

---

### Post by GlennB on 2006-08-12
Cancel that...

I blacklisted the module for the on board sound and it automagically fixed itself. After a reboot, all is well.

Glenn.

---

