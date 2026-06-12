---
title: "Soundcard E-MU 1820 not detected by Ubuntu"
date: 2009-01-26
forum: Multimedia Software
---

### Post by Zoomas on 2009-01-26
I just installed Ubuntu for the first time. Seems great, but my soundcard (Creative E-MU 1820) wasn't detected. Here is some input:

Checked if Ubuntu found my card:

```
tomas@ubuntu:~$ aplay -l
aplay: device_list:215: inga ljudkort hittades...
```

Nope. Checked that my card is recognized by the system:

```
tomas@ubuntu:~$ lspci -v
--- snip ---
04:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
	Subsystem: Creative Labs Device 4001
	Flags: medium devsel, IRQ 17
	I/O ports at ccc0 [size=32]
	Capabilities: <access denied>
	Kernel modules: snd-emu10k1
--- snip ---
```

Seems ok. Checked for ALSA version:

```
tomas@ubuntu:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.17.
```

Ok, the card should be supported. Checked if modules were present:

```
tomas@ubuntu:~$ find /lib/modules/`uname -r` | grep snd-emu10k1
/lib/modules/2.6.27-9-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.27-9-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
```

Yepp. Tried loading the proper module manually:

```
tomas@ubuntu:~$ sudo modprobe snd-emu10k1
```

No luck :(

I have no idea what to do. Read the "Comprehensive Sound Problem Solutions Guide", but that didn't help. Can someone give me a hint?

---

### Post by Zoomas on 2009-01-26
Solved! :)

Found out that "emu/hana.fw" could not be loaded and then found the solution:

[http://ubuntuforums.org/archive/index.php/t-598497.html](http://ubuntuforums.org/archive/index.php/t-598497.html)

---

