---
title: "Too many modules ?"
date: 2009-05-19
forum: Multimedia Software
---

### Post by franck31 on 2009-05-19
Hello,

I am new to ubuntu and I have installed the jaunty version. All in all everything works fine apart from the sound. It mostly works but I had a hard time installing it. I finally managed but wonder if I have not left some unnecessary modules behind.
The proper driver for my card is the hda-intel and I am using the latest alsa driver 1.0.19.
If I do a "modprobe -l | grep sound" I get the following list and that looks like an awful lot of modules.
This sound card is on the motherboard, I also have a TV card and a Hercules webcam. Can I remove some of them ?

Thanks, 

kernel/sound/soundcore.ko
kernel/sound/sound_firmware.ko
kernel/sound/oss/sound.ko
kernel/sound/oss/aedsp16.ko
kernel/sound/oss/pss.ko
kernel/sound/oss/ad1848.ko
kernel/sound/oss/mpu401.ko
kernel/sound/oss/trix.ko
kernel/sound/oss/sb_lib.ko
kernel/sound/oss/uart401.ko
kernel/sound/oss/sscape.ko
kernel/sound/oss/pas2.ko
kernel/sound/oss/sb.ko
kernel/sound/oss/kahlua.ko
kernel/sound/oss/uart6850.ko
kernel/sound/oss/opl3.ko
kernel/sound/oss/v_midi.ko
kernel/sound/oss/msnd.ko
kernel/sound/oss/msnd_classic.ko
kernel/sound/oss/msnd_pinnacle.ko
kernel/sound/pci/hda/snd-hda-intel.ko
kernel/sound/acore/snd-pcm.ko
kernel/sound/acore/seq/snd-seq.ko
kernel/sound/acore/seq/oss/snd-seq-oss.ko
kernel/sound/acore/seq/snd-seq-device.ko
kernel/sound/acore/seq/snd-seq-midi-event.ko
kernel/sound/acore/oss/snd-mixer-oss.ko
kernel/sound/acore/oss/snd-pcm-oss.ko
kernel/sound/acore/snd-hwdep.ko
kernel/sound/acore/snd.ko
kernel/sound/acore/snd-timer.ko
kernel/sound/acore/snd-page-alloc.ko
kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
kernel/sound/pci/hda/snd-hda-codec-analog.ko
kernel/sound/pci/hda/snd-hda-codec-si3054.ko
kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
kernel/sound/pci/hda/snd-hda-codec-idt.ko
kernel/sound/pci/hda/snd-hda-codec-realtek.ko
kernel/sound/pci/hda/snd-hda-codec-via.ko
kernel/sound/pci/hda/snd-hda-codec.ko
kernel/sound/pci/hda/snd-hda-codec-conexant.ko

---

### Post by franck31 on 2009-05-20
Any ideas ?

---

