---
title: "Sound card just suddenly broke!"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by doc zein on 2007-04-11
Hi. I've been using Ubuntu since about February. I have a Creative Sound Blaster Audigy 4 (non-pro) PCI soundcard and it has been working perfect UP UNTIL TODAY. I believe it has to do with some updates I installed. Whenever the orange box comes up with the updates, I install whatever updates are available (i don't usually look to see what's being updated). Anyways, I installed some updates today and had to restart Ubuntu. When I restarted (after being prompted to do so), there was NO SOUND AT ALL when ubuntu loaded up. When I clicked the Volume Control (which had a little red X box on it), it said that either I was missing Gstreamer plugins or that my sound card wasn't installed.

For some reason, my sound just broke out of the blue.

When I tried to list all the sound cards I have with sudo asoundconf list, I get NOTHING. I actually have two sound cards, an onboard Intel ICH6 and a PCI Audigy4, which was set as my default sound card.

Anyways, I re-installed alsa, and when i tried to add the module for my souncard into the kernel (with sudo modprobe snd-emu10k1), i got this message:
> WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.17-11-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.17-11-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_emu10k1 (/lib/modules/2.6.17-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for snd_emu10k1


I get the same message inserting the module ens-1371 when configuring ALSA (sudo modprobe ens-1371):
> WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.17-11-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ens1371 (/lib/modules/2.6.17-11-generic/kernel/sound/pci/snd-ens1371.ko): Unknown symbol in module, or unknown parameter (see dmesg)

and for some reason, whenever i try to open any files in gedit, this message comes up:
> ALSA lib pcm.c:2014: (snd_pcm_open_conf) Invalid type for PCM surround51 definition (id: surround51, value: cards.pcm.surround51)

i have no idea what's going on, or why my sound card just suddenly broke on ubuntu, or why all of my sound cards just disappeared. Anybody have any idea? I would really appreciate it.:confused:

---

### Post by doc zein on 2007-04-12
Help? Anyone?

---

### Post by Shinoda on 2007-04-14
Try reinstalling ALSA:```
sudo aptitude purge linux-sound-base alsa-base alsa-utils
sudo aptitude install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop
```(replace [FONT=Courier New]ubuntu-desktop[/FONT] with [FONT=Courier New]xubuntu-desktop[/FONT] if you're running Xubuntu) and reboot.

Alternatively follow e.g. [these]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#ALSA_driver_Compilation") instructions to compile it yourself.

---

