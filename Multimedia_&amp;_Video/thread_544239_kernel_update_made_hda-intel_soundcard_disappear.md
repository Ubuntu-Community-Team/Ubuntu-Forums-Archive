---
title: "kernel update made hda-intel soundcard disappear"
date: 2007-09-06
forum: Multimedia &amp; Video
---

### Post by ohme on 2007-09-06
Once upon a time I got my hda-intel card to work on the feisty. it actually worked only through headphones, but that was ok for me.

after the last update ( a few days ago) the soundcard disappeared ! 

aplay -l returns :
aplay: device_list:205: no soundcards found...

lspci -v does return (among a lot of other things)

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: LG Electronics, Inc. Unknown device 005f
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at d8500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
now,
 sudo modprobe snd-hda-intel
returns
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

getting the latest alsa files (1.0.15rc) and building successfully did not change the modprobe error.

I'm on a LG laptop machine, P1 series.

thanks ahead

---

### Post by ohme on 2007-09-07
restarting after making and installing was the missing link in the chain. you can include this in the manual.

---

