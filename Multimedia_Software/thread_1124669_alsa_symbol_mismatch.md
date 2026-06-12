---
title: "alsa symbol mismatch"
date: 2009-04-13
forum: Multimedia Software
---

### Post by alexbirkett on 2009-04-13
I'm running mythbuntu januty and I've built a patched version of alsa-source (1.0.18.dfsg-1ubuntu8 ) in order to make sound work over HDMI.

The patched driver (hda-intel) works fine. However, I'm having problems with other sound cards built into video capture cards. There appear to be mismatched symbols:

dmesg | grep symbol yelds:
```

[   12.970304] cx88_alsa: disagrees about version of symbol snd_pcm_new
[   12.970307] cx88_alsa: Unknown symbol snd_pcm_new
[   12.971308] cx88_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
[   12.971310] cx88_alsa: Unknown symbol snd_pcm_lib_ioctl
[   12.971608] cx88_alsa: disagrees about version of symbol snd_pcm_hw_constraint_pow2
[   12.971610] cx88_alsa: Unknown symbol snd_pcm_hw_constraint_pow2
[   12.971688] cx88_alsa: disagrees about version of symbol snd_pcm_set_ops
[   12.971690] cx88_alsa: Unknown symbol snd_pcm_set_ops
[   12.972313] cx88_alsa: disagrees about version of symbol snd_pcm_period_elapsed
[   12.972315] cx88_alsa: Unknown symbol snd_pcm_period_elapsed
[   21.187536] em28xx_alsa: disagrees about version of symbol snd_pcm_new
[   21.187538] em28xx_alsa: Unknown symbol snd_pcm_new
[   21.187875] em28xx_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
[   21.187877] em28xx_alsa: Unknown symbol snd_pcm_lib_ioctl
[   21.188088] em28xx_alsa: disagrees about version of symbol snd_pcm_set_ops
[   21.188090] em28xx_alsa: Unknown symbol snd_pcm_set_ops
[   21.188239] em28xx_alsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   21.188241] em28xx_alsa: Unknown symbol snd_pcm_hw_constraint_integer
[   21.188474] em28xx_alsa: disagrees about version of symbol snd_pcm_period_elapsed
[   21.188476] em28xx_alsa: Unknown symbol snd_pcm_period_elapsed


```

I've even tried building the kernel myself (ubuntu package linux-source-2.6.28 ) and then building alsa against my own kernel headers. 


Can anybody offer any advice?

Many Thanks,

Alex

---

