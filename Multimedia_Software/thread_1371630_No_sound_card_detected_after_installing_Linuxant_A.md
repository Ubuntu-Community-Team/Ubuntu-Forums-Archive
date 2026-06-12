---
title: "No sound card detected after installing Linuxant ALSA driver"
date: 2010-01-03
forum: Multimedia Software
---

### Post by yellowstar on 2010-01-03
I don't have any sound after installing Linuxant ALSA driver. I tried uninstalling it and the hsf driver, didn't help. Reinstalling ALSA didn't help either. Ubuntu doesn't detect my sound card, and aplay doesn't detect my sound card. lspci -v output for sound card:
```

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
    Subsystem: Acer Incorporated [ALI] Device 0126
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
    Memory at d0880000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [44] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
    Capabilities: [6c] HyperTransport: MSI Mapping Enable- Fixed+
    Kernel modules: snd-hda-intel

```I tried sudo modprobe snd-hda-intel, but:
```

FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

dmesg:
[ 8481.191936] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_step
[ 8481.191952] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step

```

---

### Post by Yellow Pasque on 2010-01-03
The driver may have overwritten the kernel module(s) and not restored them properly. You may want to reinstall the kernel package:
```
sudo apt-get --reinstall install linux-image-`uname -r`
```

---

### Post by yellowstar on 2010-01-03
I already tried reinstalling the kernel, and after reinstalling the kernel again, sound still doesn't work. Same error from modprobe.

---

### Post by yellowstar on 2010-01-13
I tried booting with an older kernel, but still no sound. Is it possible to reinstall Ubuntu Karmic, without reinstalling software I already installed? I'm stuck with Dial-Up, would take forever to re-download...

---

### Post by kidalabama on 2010-01-23
i have got same problem.

---

### Post by bohemier on 2010-06-16
> **Temüjin said:**
> The driver may have overwritten the kernel module(s) and not restored them properly. You may want to reinstall the kernel package:
```
sudo apt-get --reinstall install linux-image-`uname -r`
```

Thanks, that solved it for me... Had no sound after installing hsf and linuxant driver. Removed all drivers (make uninstall, dkpg -r alsa-driver-linuxant). All that was missing was to reinstall the kernel package like you mentioned.

---

### Post by ikonitas on 2010-06-26
sudo apt-get --reinstall install linux-image-`uname -r`

This did a miracle to me

---

### Post by nicktids on 2010-07-14
> sudo apt-get --reinstall install linux-image-`uname -r`


The code above installed but didn't work at first for me I then had to type the below 

sudo modprobe snd-hda-intel

After that I could then run alsamixer

Thanks for the help.

---

