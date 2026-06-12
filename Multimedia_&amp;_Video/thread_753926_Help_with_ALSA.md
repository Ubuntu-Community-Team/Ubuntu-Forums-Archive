---
title: "Help with ALSA"
date: 2008-04-13
forum: Multimedia &amp; Video
---

### Post by afderrick on 2008-04-13
I am trying to get my soundcard to work, I found the alsa drivers for it and went through the walk-through on the alsa site and didn't have a problem until one line.  I cannot find any type of help e-mails or forums on the alsa site.  So here we go.  I did the run through for my chipset found at: 
[http://www.alsa-project.org/main/index.php/Matrix:Module-oxygen](http://www.alsa-project.org/main/index.php/Matrix:Module-oxygen)
and updated my alsa-driver, alsa-lib, and alsa-utils packages up to the most current 1.0.16 version.  I have no problems installing everything and then I get to loading the modules, the line ```
sudo modprobe snd-oxygen
``` which does show up when if I type in just modprobe snd- and hit <tab> a few times.  There are a few other modules I must load and I have no problems with those, but on this one when I type it in the error I receive is: ```
FATAL: Error inserting snd_rawmidi (/lib/modules/2.6.22-14-generic/kernel/sound/acore/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_rawmidi
WARNING: Error inserting snd_mpu401_uart (/lib/modules/2.6.22-14-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_oxygen_lib (/lib/modules/2.6.22-14-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_oxygen (/lib/modules/2.6.22-14-generic/kernel/sound/pci/oxygen/snd-oxygen.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

Does anyone know what I can do to fix this?  I really want to get my sound working again!!

---

