---
title: "Sound problem emu10k1"
date: 2008-02-07
forum: Multimedia &amp; Video
---

### Post by h4ck3r on 2008-02-07
Hello,

Well, I have been working for days searching on the net trying to solve this but it won't get fixed lol... Anyway I have an SB Live sound card that requires the driver emu10k1. I some how messed up my alsa and have been trying to get it back since then (actually what I did was change sound cards.) I know for a fact that is it working because I was able to get sound with oss working although it is not as nice because not all programs are setup to use oss, so I want my alsa back where all programs use it and multiple sounds can go through at once. Anyway I have followed multiple walkthroughs. I have done atleast 4 - 5 solid walkthroughs. Anyway here is what I have.
 

lspci -v (audio only)
```


00:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
        Subsystem: Creative Labs CT4760 SBLive!
        Flags: bus master, medium devsel, latency 32, IRQ 12
        I/O ports at d000 [size=32]
        Capabilities: <access denied>

```

sudo lshw (multimedia only)

```
        *-multimedia UNCLAIMED
             description: Multimedia audio controller
             product: SB Live! EMU10k1
             vendor: Creative Labs
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32 maxlatency=20 mingnt=2

```

sudo modprobe snd-emu10k1

```
FATAL: Error inserting snd (/lib/modules/2.6.22-14-386/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.22-14-386/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.22-14-386/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.22-14-386/kernel/sound/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.22-14-386/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.22-14-386/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.22-14-386/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.22-14-386/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.22-14-386/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.22-14-386/kernel/sound/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_rawmidi (/lib/modules/2.6.22-14-386/kernel/sound/acore/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_rawmidi
FATAL: Error inserting snd (/lib/modules/2.6.22-14-386/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.22-14-386/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.22-14-386/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.22-14-386/kernel/sound/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.22-14-386/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.22-14-386/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.22-14-386/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.22-14-386/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.22-14-386/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.22-14-386/kernel/sound/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_rawmidi (/lib/modules/2.6.22-14-386/kernel/sound/acore/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_rawmidi
FATAL: Error inserting snd_emu10k1 (/lib/modules/2.6.22-14-386/kernel/sound/pci/emu10k1/snd-emu10k1.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for snd_emu10k1
```

I have reinstalled the sound system many times with purge, made it from source plus lots of other stuff. Any suggestions or even ways of doing what I have done more fully would be appreciated. Thanks

---

### Post by h4ck3r on 2008-02-07
bump

---

### Post by h4ck3r on 2008-02-07
bump

---

### Post by h4ck3r on 2008-02-07
Any ideas on a way of fixing the sound?

---

