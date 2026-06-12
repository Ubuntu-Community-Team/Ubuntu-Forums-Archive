---
title: "Sound Issues for 9.10 Upgrade"
date: 2009-11-11
forum: Multimedia Software
---

### Post by Unspoken on 2009-11-11
I have went through the comprehensive guide a few times, and I can't seem to get sound to work on my recently updated 9.10. I had no problems with sound in 9.04, so this is rather irritating that the newest version cannot seem to grasp this.

I am using an onboard Nvidia HDA setup. I have no devices for sound when I try "aplay -l". Here's the info for the audio that the lspci gives me:

```
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Device 399a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at f9f78000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

I want to believe that it has something to do with the headers I have for this distribution. When I use the alsa-source and the manager to edit it, as soon as I try to finish it up, it tells me that it can't find linux-headers-2.6.28-11-generic. Ubuntu won't let me reinstall that version, seeing as how I think it has 2.6.31 installed as well. Also, when I try to run alsamixer, it isn't found on my computer, even after constant installings from the package manager.

I'm still not even close to being savvy with Linux, so any help would be appreciated.

---

### Post by Ulysses361 on 2009-11-13
Please send us output from step 3 and step 4 from this procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Please also specify the exact model and make of pc that you are using.

---

