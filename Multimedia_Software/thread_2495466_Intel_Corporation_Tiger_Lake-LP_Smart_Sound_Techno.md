---
title: "Intel Corporation Tiger Lake-LP Smart Sound Technology Audio  No sound issue"
date: 2024-02-20
forum: Multimedia Software
---

### Post by dargy on 2024-02-20
I fresh installed Ubuntu 23.10, after installation process there is no sound from my speaker. 

lspci -nnk | grep -A2 Audio -> give me that result belove.
00:1f.3 Multimedia audio controller [0401]: Intel Corporation Tiger Lake-LP Smart Sound Technology Audio Controller [8086:a0c8] (rev 20)
    Subsystem: IP3 Tech (HK) Limited Tiger Lake-LP Smart Sound Technology Audio Controller [1e50:6004]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_sof_pci_intel_tgl


I tried a few solutions but not works. I was installed Fedora before, everything was fine. What should i missing or what can i do to get sound from my speaker? Im very newbie in linux, could you please refer me to fix it?

Tried solutions
1- 
sudo alsa force-reload
sudo nano /etc/default/grub
**GRUB_CMDLINE_LINUX_DEFAULT = **snd_intel_dspcfg.dsp_driver=1

2-
sudo apt-get remove --purge alsa-base pulseaudio
sudo apt-get install alsa-base pulseaudio
sudo alsa force-reload

both not work unfortunately

---

