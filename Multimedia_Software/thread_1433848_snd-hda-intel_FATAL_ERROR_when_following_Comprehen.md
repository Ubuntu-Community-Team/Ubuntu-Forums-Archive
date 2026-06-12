---
title: "snd-hda-intel FATAL ERROR when following Comprehensive Sound Problems Thread"
date: 2010-03-19
forum: Multimedia Software
---

### Post by OniLink10 on 2010-03-19
I have been following [this](http://ubuntuforums.org/showthread.php?t=205449) thread to fix up my sound card(it decided to stop being detected). The first time I reached step 4, I had to go compile ALSA from source. Now I'm back at Step 4 and I'm recieving this error:
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.31-20-generic/updates/alsa/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
dmesg gives this:
[52574.050336] snd_hda_codec: Unknown symbol snd_ctl_boolean_mono_info
[52574.050764] snd_hda_codec: Unknown symbol snd_hidden_kstrdup
[52574.051006] snd_hda_codec: disagrees about version of symbol _snd_ctl_add_slave
[52574.051010] snd_hda_codec: Unknown symbol _snd_ctl_add_slave
[52574.051203] snd_hda_codec: disagrees about version of symbol snd_pci_quirk_lookup
[52574.051207] snd_hda_codec: Unknown symbol snd_pci_quirk_lookup
[52574.051408] snd_hda_codec: Unknown symbol snd_hidden_kmalloc
[52574.051591] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_step
[52574.051595] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[52574.051756] snd_hda_codec: Unknown symbol snd_hidden_kstrndup
What could I be doing wrong? What started as a few frequencies missing on Youtube videos has scaled into a catastrophe! :confused:
My sound card is a Intel ICH10 onboard, and my Ubuntu version is x64 9.10.

---

### Post by OniLink10 on 2010-03-19
Anyone?

---

### Post by OniLink10 on 2010-03-20
Hello? I really need help here.

---

### Post by Yellow Pasque on 2010-03-20
Those directions are outdated. Use this to build ALSA from source: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by OniLink10 on 2010-03-20
It works! Thank you so much!

---

