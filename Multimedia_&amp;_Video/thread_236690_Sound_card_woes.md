---
title: "Sound card woes"
date: 2006-08-15
forum: Multimedia &amp; Video
---

### Post by ChriX on 2006-08-15
Hi all,

I've got a Ubuntu server install on my machine and am now trying to get the sound card to work. I have tried following the guide at the top of the forum, but still I get no soundcards detected when trying aplay -l.

I think I managed to successfully compile the module, but when I try and load it I get the following:
```
root@stable1:/home/admin# modprobe snd-ens1371
FATAL: Error inserting snd (/lib/modules/2.6.15-23-server/updates/alsa/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.15-23-server/updates/alsa/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.15-23-server/updates/alsa/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.15-23-server/updates/alsa/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.15-23-server/updates/alsa/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.15-23-server/updates/alsa/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.15-23-server/updates/alsa/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.15-23-server/kernel/sound/acore/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ens1371 (/lib/modules/2.6.15-23-server/kernel/sound/pci/snd-ens1371.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

Dmesg shows lots of 'Unknown symbol' errors, too many to paste in. The following is the lspci output for my card:

```
0000:01:0d.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
        Subsystem: Ensoniq Creative Sound Blaster AudioPCI64V, AudioPCI128
        Flags: bus master, slow devsel, latency 96, IRQ 10
        I/O ports at 3000 [disabled] [size=64]
        Capabilities: [dc] Power Management version 1

```

Any advice appreciated!

---

