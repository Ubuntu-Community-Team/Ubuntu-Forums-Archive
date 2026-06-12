---
title: "Sound Help? - Cirrus Logic Sound Fusion CS46XX"
date: 2006-12-02
forum: Multimedia &amp; Video
---

### Post by tux-curious on 2006-12-02
Sorry if this is in the wrong place.

Hey, my goal for the day was to get sound on my box and well.. isn't going so well. Lol, part way through I got frustrated and completely reinstalled edgy.

*I have had sound before on this box, once. It worked with SUSE, but it didn't have a debian base.*

I went through the Comprehensive Sound Guide and have learned that:
[LIST]
[*]"aplay -l" tells me that I have no sound card installed
[*]"lspci -v" tells me I'm running the cd46xx
[*]The ALSA database has the driver for the sound card, or at least apears to ([http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Cirrus+Logic&card=.&chip=CS4280%2C+CS4610%2C+CS4612%2C+CS4614%2C+CS4615%2C+CS4622%2C+CS4624%2C+CS4630&module=cs46xx](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Cirrus+Logic&card=.&chip=CS4280%2C+CS4610%2C+CS4612%2C+CS4614%2C+CS4615%2C+CS4622%2C+CS4624%2C+CS4630&module=cs46xx))
[/LIST]

Edit: New info below!

---

### Post by tux-curious on 2006-12-03
So I went to the "ALSA Driver Compilation" section and followed through it, using the alsa-source, and module-assistant. It seemed to work, I think.. but then I went back and typed in "sudo modprobe snd-cs46xx" and it gave me:

```
steven@steven-desktop:~$ sudo modprobe snd-cs46xx
Password:
FATAL: Error inserting snd (/lib/modules/2.6.17-10-generic/updates/alsa/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.17-10-generic/updates/alsa/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.17-10-generic/updates/alsa/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.17-10-generic/updates/alsa/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.17-10-generic/updates/alsa/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.17-10-generic/updates/alsa/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.17-10-generic/updates/alsa/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.17-10-generic/updates/alsa/acore/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_cs46xx (/lib/modules/2.6.17-10-generic/updates/alsa/pci/cs46xx/snd-cs46xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

It told me that if ALSA Driver compilation didn't work I should post here, so here I am.

---

