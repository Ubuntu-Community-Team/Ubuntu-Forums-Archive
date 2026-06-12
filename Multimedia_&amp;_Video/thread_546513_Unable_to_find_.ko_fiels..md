---
title: "Unable to find .ko fiels."
date: 2007-09-08
forum: Multimedia &amp; Video
---

### Post by arm-c on 2007-09-08
I am trying to configure my sound card, however, the modprobe returns errors, that it is unable to find the .ko files.

>> QUESTION:  How do I point MODPROBE to the correct location of the sound .ko files?

These files do exist, but the program is looking in the following location:

/lib/modules/2.6.20-15-generic/kernel/sound/

when the files it wants are in the:
/lib/modules/2.6.20-15-386/kernel/sound/

OUTPUT FROM THE MODPROBE FILE:
modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd-pcm.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/isa/cs423x/snd-cs4231-lib.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/seq/snd-seq-device.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd-rawmidi.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/isa/cs423x/snd-cs4236-lib.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd-hwdep.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/isa/cs423x/snd-cs4236.ko': No such file or directory

---

