---
title: "Kernel upgrade broke my sound (snd-hda-intel)"
date: 2006-09-16
forum: Multimedia &amp; Video
---

### Post by martinrandau on 2006-09-16
After the latest kernel upgrade my sound no longer works. I see a cross above the speaker in the upper right corner. 

modprobe snd-hda-intel gives this:
```
martin@yeah:~$ sudo modprobe snd-hda-intel
WARNING: Error inserting snd_timer (/lib/modules/2.6.15-26-686/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.15-26-686/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.15-26-686/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.15-26-686/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.15-26-686/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

```
martin@yeah:~$ dmesg | tail
[17179911.120000] snd_hda_intel: Unknown symbol snd_hda_calc_stream_format
[17179911.120000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[17179911.120000] snd_hda_intel: Unknown symbol snd_hda_suspend
[17179911.120000] snd_hda_intel: disagrees about version of symbol snd_device_new
[17179911.120000] snd_hda_intel: Unknown symbol snd_device_new
[17179911.120000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[17179911.120000] snd_hda_intel: Unknown symbol snd_hda_resume
[17179911.120000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[17179911.120000] snd_hda_intel: Unknown symbol snd_hda_build_controls
[17179911.120000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed

```

The kernel recognizes my sound card:
```
martin@yeah:~$ lspci | grep Audio
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

This is really annoying as I have had a really hard time getting my sound to work on my Acer Aspire 5600 laptop. I had to use a special path. It ran for two weeks and then comes this update and ruins it again. 

Why isn't the snd-hda-intel module in the kernel???

---

### Post by martinrandau on 2006-09-16
Never mind it not being in kernel, I downloaded and installed the latest alsa-drivers and got sound now again. 

Still, shame on those that are responsible... no, not really, I love what you are doing to linux. :lol:

---

