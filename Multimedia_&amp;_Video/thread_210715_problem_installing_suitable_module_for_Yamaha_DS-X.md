---
title: "problem installing suitable module for Yamaha DS-XG"
date: 2006-07-07
forum: Multimedia &amp; Video
---

### Post by _Haiku_ on 2006-07-07
Hi there,

I just install my first Ubuntu yesterday night. First of all, it's an impressive distrib, so congrat to the community for doing such a great job.

I do have a problem with my sound card, which is a Yamaha (:-k) DS-XG 724.

I read the guide "Comprehensive Sound Problem Solutions Guide v0.5a", that helps me alot, but I still have an error.

I follow the guide step by step, compiling the snd-ymfpci ALSA driver, but when I do "sudo modprobe snd-ymfpci", I get the following error:

```

FATAL: Error inserting snd_pcm (/lib/modules/2.6.15-23-386/updates/alsa/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.15-23-386/updates/alsa/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ymfpci (/lib/modules/2.6.15-23-386/updates/alsa/pci/ymfpci/snd-ymfpci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

with the following dmesg log : 

```

[4312989.827000] snd_pcm: Unknown symbol snd_verbose_printd
[4312989.827000] snd_pcm: Unknown symbol snd_hidden_kzalloc
[4312989.828000] snd_pcm: disagrees about version of symbol snd_timer_notify
[4312989.828000] snd_pcm: Unknown symbol snd_timer_notify
[4312989.828000] snd_pcm: disagrees about version of symbol snd_timer_interrupt
[4312989.828000] snd_pcm: Unknown symbol snd_timer_interrupt
[4312989.829000] snd_pcm: Unknown symbol snd_hidden_kcalloc
[4312989.829000] snd_pcm: Unknown symbol snd_hidden_kfree
[4312989.829000] snd_pcm: Unknown symbol snd_verbose_printk
[4312989.830000] snd_pcm: disagrees about version of symbol snd_timer_new
[4312989.830000] snd_pcm: Unknown symbol snd_timer_new
[4312989.830000] snd_pcm: Unknown symbol snd_hidden_kmalloc
[4312989.834000] snd_ac97_codec: Unknown symbol snd_hidden_kzalloc
[4312989.835000] snd_ac97_codec: Unknown symbol snd_hidden_kcalloc
[4312989.835000] snd_ac97_codec: Unknown symbol snd_interval_refine
[4312989.835000] snd_ac97_codec: Unknown symbol snd_hidden_kfree
[4312989.835000] snd_ac97_codec: Unknown symbol snd_verbose_printk
[4312989.836000] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[4312989.838000] snd_ymfpci: Unknown symbol snd_hidden_kzalloc
[4312989.838000] snd_ymfpci: Unknown symbol snd_ac97_resume
[4312989.839000] snd_ymfpci: Unknown symbol snd_pcm_new
[4312989.839000] snd_ymfpci: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[4312989.839000] snd_ymfpci: Unknown symbol snd_pcm_hw_constraint_minmax
[4312989.839000] snd_ymfpci: disagrees about version of symbol snd_timer_interrupt
[4312989.840000] snd_ymfpci: Unknown symbol snd_timer_interrupt
[4312989.840000] snd_ymfpci: Unknown symbol snd_hidden_kcalloc
[4312989.840000] snd_ymfpci: Unknown symbol snd_ac97_update_bits
[4312989.840000] snd_ymfpci: Unknown symbol snd_hidden_kfree
[4312989.840000] snd_ymfpci: Unknown symbol snd_ac97_mixer
[4312989.841000] snd_ymfpci: disagrees about version of symbol snd_opl3_create
[4312989.841000] snd_ymfpci: Unknown symbol snd_opl3_create
[4312989.841000] snd_ymfpci: Unknown symbol snd_ac97_bus
[4312989.841000] snd_ymfpci: Unknown symbol snd_verbose_printk
[4312989.842000] snd_ymfpci: Unknown symbol snd_ac97_suspend
[4312989.842000] snd_ymfpci: Unknown symbol snd_pcm_lib_malloc_pages
[4312989.842000] snd_ymfpci: Unknown symbol snd_pcm_lib_ioctl
[4312989.842000] snd_ymfpci: Unknown symbol snd_pcm_lib_free_pages
[4312989.843000] snd_ymfpci: Unknown symbol snd_pcm_set_ops
[4312989.843000] snd_ymfpci: disagrees about version of symbol snd_timer_new
[4312989.843000] snd_ymfpci: Unknown symbol snd_timer_new
[4312989.843000] snd_ymfpci: Unknown symbol snd_pcm_suspend_all
[4312989.844000] snd_ymfpci: disagrees about version of symbol snd_mpu401_uart_new
[4312989.844000] snd_ymfpci: Unknown symbol snd_mpu401_uart_new
[4312989.844000] snd_ymfpci: Unknown symbol snd_pcm_lib_preallocate_free_for_all
[4312989.844000] snd_ymfpci: disagrees about version of symbol snd_opl3_hwdep_new
[4312989.845000] snd_ymfpci: Unknown symbol snd_opl3_hwdep_new
[4312989.845000] snd_ymfpci: Unknown symbol snd_pcm_period_elapsed
[4312989.845000] snd_ymfpci: Unknown symbol snd_pcm_format_width

```

I'm quite lost at this point, so I'm looking for some help or pointer to get further.

---

