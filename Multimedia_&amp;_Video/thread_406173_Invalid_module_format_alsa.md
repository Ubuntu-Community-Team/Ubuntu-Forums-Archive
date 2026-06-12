---
title: "Invalid module format alsa"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by madubuntuer on 2007-04-10
I using an onboard ALC850 chipset which am try to setup 5.1 with. I thought I give alsa a shot but after installing it it wont let me insert the modules.
tarting sound driver: snd-intel8x0 WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.15-27-amd64-generic/kernel/sound/acore/snd-page-alloc.ko): Invalid module format
FATAL: Error inserting snd (/lib/modules/2.6.15-27-amd64-generic/kernel/sound/acore/snd.ko): Invalid module format
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.15-27-amd64-generic/kernel/sound/acore/snd-timer.ko): Invalid module format
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.15-27-amd64-generic/kernel/sound/acore/snd-page-alloc.ko): Invalid module format
FATAL: Error inserting snd (/lib/modules/2.6.15-27-amd64-generic/kernel/sound/acore/snd.ko): Invalid module format
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.15-27-amd64-generic/kernel/sound/acore/snd-timer.ko): Invalid module format
FATAL: Error inserting snd_pcm (/lib/modules/2.6.15-27-amd64-generic/kernel/sound/acore/snd-pcm.ko): Invalid module format
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_bus (/lib/modules/2.6.15-27-amd64-generic/kernel/sound/pci/ac97/snd-ac97-bus.ko): Invalid module format
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.15-27-amd64-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko): Invalid module format
FATAL: Error inserting snd_intel8x0 (/lib/modules/2.6.15-27-amd64-generic/kernel/sound/pci/snd-intel8x0.ko): Invalid module format
done
 
I noticed it used GCC3.4 but isn't the kernel for dapper compiled with GCC4?

---

### Post by revoman3 on 2007-06-04
i have the same problem with my ca106 sound card. I think the latest versions of alsa do not function correctly. I have dapper but alsa automaticly updated now im stuck with no sound!

---

### Post by revoman3 on 2007-06-04
michael@michael-desktop:~$ sudo modprobe snd-ca0106
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.15-28-386/updates/alsa/acore/snd-page-alloc.ko): Invalid module format
WARNING: Error inserting snd_ac97_bus (/lib/modules/2.6.15-28-386/updates/alsa/pci/ac97/snd-ac97-bus.ko): Invalid module format
FATAL: Error inserting snd (/lib/modules/2.6.15-28-386/updates/alsa/acore/snd.ko): Invalid module format
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.15-28-386/updates/alsa/acore/snd-timer.ko): Invalid module format
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.15-28-386/updates/alsa/acore/snd-page-alloc.ko): Invalid module format
FATAL: Error inserting snd (/lib/modules/2.6.15-28-386/updates/alsa/acore/snd.ko): Invalid module format
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.15-28-386/updates/alsa/acore/snd-timer.ko): Invalid module format
FATAL: Error inserting snd_pcm (/lib/modules/2.6.15-28-386/updates/alsa/acore/snd-pcm.ko): Invalid module format
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.15-28-386/updates/alsa/pci/ac97/snd-ac97-codec.ko): Invalid module format
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.15-28-386/updates/alsa/acore/seq/snd-seq-device.ko): Invalid module format
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.15-28-386/updates/alsa/acore/snd-rawmidi.ko): Invalid module format
FATAL: Error inserting snd_ca0106 (/lib/modules/2.6.15-28-386/updates/alsa/pci/ca0106/snd-ca0106.ko): Invalid module format
michael@michael-desktop:~$

---

