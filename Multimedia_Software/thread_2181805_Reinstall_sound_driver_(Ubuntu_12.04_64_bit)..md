---
title: "Reinstall sound driver (Ubuntu 12.04 64 bit)."
date: 2013-10-19
forum: Multimedia Software
---

### Post by lucacerone on 2013-10-19
Hi everybody,
after messing up witho Gnome and Unity packages (which now I managed to reinstall)
the sound on my computer is gone. I have Ubuntu 12.04 64 bit

The problem is that if I click on the "sound" icon, 
the sound card is not recognized (the hardware only shows dummy output).

But if I type ```
lspci -v
``` the audio device appears in the output:

> 00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
	Subsystem: Samsung Electronics Co Ltd Device c0d8
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at c0210000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

Following some guide I have tried to give the two commands:
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```

but this didn't solve the issue.

How can I reinstall the drivers for my sound card and get the sound back? 
(when I install Ubuntu from scratch everything works just fine,
so if I just could purge the installed packages and reinstall them 
from scratch everything should work fine).

Thanks a lot in advance to all of you for the help.
Cheers,
Luca

---

### Post by Yellow Pasque on 2013-10-19
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by lucacerone on 2013-10-20
Hi Temujin,
thanks for the answer. I was actually looking at some easier configuration, I just need to find the packages that need to reinstalled and configured.

Anyway I partially solved the issue by reinstalling pulseaudio and related packages. I say partially because now the sound works just fine, but 
in the sound settings non display is shown (not even the dummy one).

How can I manage to get the hardware listed again? Should I try the package from the link you sent, or it is overkill in this case?

Thanks a lot again for the help!

Cheers,
Luca

---

