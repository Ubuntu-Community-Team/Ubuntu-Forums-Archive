---
title: "m-audio delta 66 and delta 1010 installation?"
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by umbrAtrorum on 2006-08-08
hi!

i tried to setup ubuntu 6.06 for my two sound cards, m-audio delta 66 and delta 1010. first i tried the installation of the oss-drivers, which fairly succeeded and even played some sounds in the test phase, only i didn't get any access to sound mixing or selecting the sound cards as default in the system>preferences>sound dialogue. so i removed them and started installing the alsa drivers as described on their page (basically building all parts of the installation as modules and then inserting them via modprobe). this is where he rewfuses to do anything. for every module he gives the message

WARNING: Error inserting snd_timer (/lib/modules/2.6.15-26-386/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_seq (/lib/modules/2.6.15-26-386/kernel/sound/acore/seq/snd-seq.ko): Unknown symbol in module, or unknown parameter (see dmesg)

so i got two questions now:

1. which driver would you recommend? oss or alsa?

2. how do i PROPERLY set up the recommended driver?

i'd be f***ing grateful for help. thx.

jaspeR

---

### Post by umbrAtrorum on 2006-08-08
i now followed the Comprehensive Sound Problem Solutions Guide v0.5e on this forum. it worked up to the point where i was supposed to install the alsa driver via modprobe snd-ice1712. again, the error message reads:

FATAL: Error inserting snd_pcm (/lib/modules/2.6.15-26-386/updates/alsa/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.15-26-386/updates/alsa/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ice1712 (/lib/modules/2.6.15-26-386/updates/alsa/pci/ice1712/snd-ice1712.ko): Unknown symbol in module, or unknown parameter (see dmesg)

help please?

---

