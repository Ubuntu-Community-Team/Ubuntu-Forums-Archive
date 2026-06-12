---
title: "Trouble with compiling and loading snd-geode module"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by McAviti on 2007-07-29
Hi!

Since several new kernel versions I try to compile the source for the sound module for my Mini-ITX PC, using the drivers pack from AMD. I currently have the recent 2.6.15.28 sources and the ALSA src packe, with i both compiled manually. (Tried with and without ALSA source.)
The Ubuntu installation itself is a 6.06 LTS.

So, the sources of the Geode sound module compile well ([http://www.amd.com/us-en/ConnectivitySolutions/TechnicalResources/0,,50_2334_2452_11363,00.html](http://www.amd.com/us-en/ConnectivitySolutions/TechnicalResources/0,,50_2334_2452_11363,00.html)), but when I try to load the module, i receive the following lines in the log:
--
Jul 29 12:09:14 maccaroni kernel: [18956939.456000] snd_geode: Unknown symbol snd_ac97_resume
Jul 29 12:09:14 maccaroni kernel: [18956939.456000] snd_geode: Unknown symbol snd_pcm_new
Jul 29 12:09:14 maccaroni kernel: [18956939.456000] snd_geode: Unknown symbol snd_card_register
Jul 29 12:09:14 maccaroni kernel: [18956939.456000] snd_geode: Unknown symbol snd_card_free
Jul 29 12:09:14 maccaroni kernel: [18956939.456000] snd_geode: Unknown symbol snd_ac97_mixer
Jul 29 12:09:14 maccaroni kernel: [18956939.456000] snd_geode: Unknown symbol snd_card_pci_resume
Jul 29 12:09:14 maccaroni kernel: [18956939.456000] snd_geode: Unknown symbol snd_ac97_bus
Jul 29 12:09:14 maccaroni kernel: [18956939.460000] snd_geode: Unknown symbol snd_card_new
Jul 29 12:09:14 maccaroni kernel: [18956939.460000] snd_geode: Unknown symbol snd_ac97_suspend
Jul 29 12:09:14 maccaroni kernel: [18956939.460000] snd_geode: Unknown symbol snd_pcm_lib_malloc_pages
Jul 29 12:09:14 maccaroni kernel: [18956939.460000] snd_geode: Unknown symbol snd_pcm_lib_ioctl
Jul 29 12:09:14 maccaroni kernel: [18956939.460000] snd_geode: Unknown symbol snd_pcm_lib_free_pages
Jul 29 12:09:14 maccaroni kernel: [18956939.460000] snd_geode: Unknown symbol snd_card_pci_suspend
Jul 29 12:09:14 maccaroni kernel: [18956939.460000] snd_geode: Unknown symbol snd_pcm_set_ops
Jul 29 12:09:14 maccaroni kernel: [18956939.460000] snd_geode: Unknown symbol snd_card_set_pm_callback
Jul 29 12:09:14 maccaroni kernel: [18956939.460000] snd_geode: Unknown symbol snd_pcm_hw_constraint_list
Jul 29 12:09:14 maccaroni kernel: [18956939.460000] snd_geode: Unknown symbol snd_device_new
Jul 29 12:09:14 maccaroni kernel: [18956939.460000] snd_geode: Unknown symbol snd_pcm_suspend_all
Jul 29 12:09:14 maccaroni kernel: [18956939.460000] snd_geode: Unknown symbol snd_pcm_lib_preallocate_pages
Jul 29 12:09:14 maccaroni kernel: [18956939.460000] snd_geode: Unknown symbol snd_pcm_period_elapsed
--

I'd appreciate very much if anybody could help me, my ears dry out due to lack of music...
thanx,
klemens

---

