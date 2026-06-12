---
title: "No sound after update"
date: 2010-06-23
forum: Multimedia Software
---

### Post by blackmath on 2010-06-23
I updated my system (10.04) today with Update Manager and now I have no sound. I followed the steps given in [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449") including compiling the driver (which is the standard intel one) - nothing. I get:

```
FATAL: Error inserting snd_intel8x0 (/lib/modules/2.6.32-22-generic/updates/alsa/pci/snd-intel8x0.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

dmseg say:

```
[  105.946016] snd_ac97_codec: disagrees about version of symbol snd_info_register
[  105.946027] snd_ac97_codec: Unknown symbol snd_info_register
[  105.946382] snd_ac97_codec: disagrees about version of symbol snd_ctl_add
[  105.946388] snd_ac97_codec: Unknown symbol snd_ctl_add
[  105.946753] snd_ac97_codec: disagrees about version of symbol snd_info_free_entry
[  105.946759] snd_ac97_codec: Unknown symbol snd_info_free_entry
[  105.947200] snd_ac97_codec: disagrees about version of symbol snd_ctl_find_id...

```

What now ? That's 45 mins wasted - please don't say reinstall - life's too short :-)

---

### Post by Yellow Pasque on 2010-06-23
Either reinstall alsa or compile the right way (specifically, you need a new kernel midule that matches the kernel you probably updated): [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by blackmath on 2010-06-23
i did update the kernel - that's when the sound stopped working.

so the driver I had doesn't work with the new kernel ? why doesn't the update get the new driver too ?

---

### Post by Yellow Pasque on 2010-06-23
> why doesn't the update get the new driver too ?
..because the Ubuntu version of the kernel module was made with a specific version of ALSA, and now you're building a different version.

---

