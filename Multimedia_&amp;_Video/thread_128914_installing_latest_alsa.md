---
title: "installing latest alsa"
date: 2006-02-12
forum: Multimedia &amp; Video
---

### Post by jeremytaylor on 2006-02-12
Hi,

I've got an audigy 2 pcmcia sound card and I noticed that the latest development release of alsa is supposed to support this card. 

I've tried installing from source but haven't had much luck, 
In particular dmesg gives
snd_rawmidi: Unknown symbol snd_device_register
[4294701.904000] snd_rawmidi: disagrees about version of symbol snd_register_device
[4294701.904000] snd_rawmidi: Unknown symbol snd_register_device
[4294701.908000] snd_hwdep: disagrees about version of symbol snd_info_register
[4294701.908000] snd_hwdep: Unknown symbol snd_info_register
[4294701.908000] snd_hwdep: disagrees about version of symbol snd_info_create_module_entry
[4294701.909000] snd_hwdep: Unknown symbol snd_info_create_module_entry
[4294701.909000] snd_hwdep: disagrees about version of symbol snd_info_free_entry
[4294701.909000] snd_hwdep: Unknown symbol snd_info_free_entry
[4294701.909000] snd_hwdep: disagrees about version of symbol snd_unregister_oss_device
[4294701.909000] snd_hwdep: Unknown symbol snd_unregister_oss_device
[4294701.909000] snd_hwdep: disagrees about version of symbol snd_register_oss_device
[4294701.909000] snd_hwdep: Unknown symbol snd_register_oss_device
[4294701.909000] snd_hwdep: disagrees about version of symbol snd_ctl_register_ioctl
[4294701.909000] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[4294701.909000] snd_hwdep: disagrees about version of symbol snd_card_file_add
[4294701.909000] snd_hwdep: Unknown symbol snd_card_file_add
[4294701.909000] snd_hwdep: Unknown symbol snd_compat_kzalloc
[4294701.909000] snd_hwdep: disagrees about version of symbol snd_iprintf
[4294701.909000] snd_hwdep: Unknown symbol snd_iprintf
[4294701.909000] snd_hwdep: disagrees about version of symbol snd_unregister_device
[4294701.909000] snd_hwdep: Unknown symbol snd_unregister_device
[4294701.909000] snd_hwdep: disagrees about version of symbol snd_device_new
[4294701.909000] snd_hwdep: Unknown symbol snd_device_new
[4294701.909000] snd_hwdep: disagrees about version of symbol snd_ctl_unregister_ioctl
[4294701.909000] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[4294701.909000] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data
[4294701.909000] snd_hwdep: Unknown symbol snd_lookup_minor_data
[4294701.909000] snd_hwdep: disagrees about version of symbol snd_card_file_remove
[4294701.909000] snd_hwdep: Unknown symbol snd_card_file_remove
[4294701.909000] snd_hwdep: disagrees about version of symbol snd_info_unregister
[4294701.909000] snd_hwdep: Unknown symbol snd_info_unregister
[4294701.909000] snd_hwdep: disagrees about version of symbol snd_register_device
[4294701.909000] snd_hwdep: Unknown symbol snd_register_device
[4294701.909000] snd_util_mem: Unknown symbol snd_compat_kzalloc
[4294701.910000] snd_ac97_codec: disagrees about version of symbol snd_info_register
[4294701.910000] snd_ac97_codec: Unknown symbol snd_info_register
[4294701.910000] snd_ac97_codec: disagrees about version of symbol snd_ctl_add
[4294701.910000] snd_ac97_codec: Unknown symbol snd_ctl_add
[4294701.910000] snd_ac97_codec: disagrees about version of symbol snd_info_free_entry
[4294701.910000] snd_ac97_codec: Unknown symbol snd_info_free_entry
[4294701.910000] snd_ac97_codec: disagrees about version of symbol snd_interval_refine
[4294701.910000] snd_ac97_codec: Unknown symbol snd_interval_refine
[4294701.910000] snd_ac97_codec: disagrees about version of symbol snd_ctl_find_id
[4294701.910000] snd_ac97_codec: Unknown symbol snd_ctl_find_id
[4294701.910000] snd_ac97_codec: disagrees about version of symbol snd_ctl_new1
[4294701.910000] snd_ac97_codec: Unknown symbol snd_ctl_new1
[4294701.910000] snd_ac97_codec: disagrees about version of symbol snd_ctl_remove_id
[4294701.910000] snd_ac97_codec: Unknown symbol snd_ctl_remove_id
[4294701.910000] snd_ac97_codec: disagrees about version of symbol snd_component_add
[4294701.910000] snd_ac97_codec: Unknown symbol snd_component_add
[4294701.910000] snd_ac97_codec: disagrees about version of symbol snd_pcm_hw_rule_add
[4294701.910000] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[4294701.910000] snd_ac97_codec: Unknown symbol snd_compat_kzalloc
[4294701.910000] snd_ac97_codec: disagrees about version of symbol snd_iprintf
[4294701.910000] snd_ac97_codec: Unknown symbol snd_iprintf
[4294701.910000] snd_ac97_codec: disagrees about version of symbol snd_device_new
[4294701.910000] snd_ac97_codec: Unknown symbol snd_device_new
[4294701.911000] snd_ac97_codec: disagrees about version of symbol snd_info_create_card_entry
[4294701.911000] snd_ac97_codec: Unknown symbol snd_info_create_card_entry
[4294701.911000] snd_ac97_codec: disagrees about version of symbol snd_info_unregister
[4294701.911000] snd_ac97_codec: Unknown symbol snd_info_unregister
[4294701.911000] snd_rawmidi: disagrees about version of symbol snd_info_register
[4294701.911000] snd_rawmidi: Unknown symbol snd_info_register
[4294701.911000] snd_rawmidi: disagrees about version of symbol snd_seq_device_new
[4294701.911000] snd_rawmidi: Unknown symbol snd_seq_device_new
[4294701.911000] snd_rawmidi: disagrees about version of symbol snd_info_free_entry
[4294701.911000] snd_rawmidi: Unknown symbol snd_info_free_entry
[4294701.911000] snd_rawmidi: disagrees about version of symbol snd_unregister_oss_device
[4294701.911000] snd_rawmidi: Unknown symbol snd_unregister_oss_device
[4294701.911000] snd_rawmidi: disagrees about version of symbol snd_register_oss_device
[4294701.911000] snd_rawmidi: Unknown symbol snd_register_oss_device
[4294701.911000] snd_rawmidi: disagrees about version of symbol snd_ctl_register_ioctl
[4294701.911000] snd_rawmidi: Unknown symbol snd_ctl_register_ioctl
[4294701.911000] snd_rawmidi: disagrees about version of symbol snd_card_file_add
[4294701.911000] snd_rawmidi: Unknown symbol snd_card_file_add
[4294701.911000] snd_rawmidi: Unknown symbol snd_compat_kzalloc
[4294701.911000] snd_rawmidi: disagrees about version of symbol snd_iprintf
[4294701.911000] snd_rawmidi: Unknown symbol snd_iprintf
[4294701.911000] snd_rawmidi: disagrees about version of symbol snd_unregister_device
[4294701.911000] snd_rawmidi: Unknown symbol snd_unregister_device
[4294701.911000] snd_rawmidi: disagrees about version of symbol snd_device_new
[4294701.911000] snd_rawmidi: Unknown symbol snd_device_new
[4294701.911000] snd_rawmidi: disagrees about version of symbol snd_ctl_unregister_ioctl
[4294701.911000] snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl
[4294701.911000] snd_rawmidi: Unknown symbol snd_lookup_oss_minor_data
[4294701.911000] snd_rawmidi: Unknown symbol snd_lookup_minor_data
[4294701.911000] snd_rawmidi: disagrees about version of symbol snd_info_create_card_entry
[4294701.911000] snd_rawmidi: Unknown symbol snd_info_create_card_entry
[4294701.912000] snd_rawmidi: disagrees about version of symbol snd_device_free
[4294701.912000] snd_rawmidi: Unknown symbol snd_device_free
[4294701.912000] snd_rawmidi: disagrees about version of symbol snd_card_file_remove
[4294701.912000] snd_rawmidi: Unknown symbol snd_card_file_remove
[4294701.912000] snd_rawmidi: disagrees about version of symbol snd_info_unregister
[4294701.912000] snd_rawmidi: Unknown symbol snd_info_unregister
[4294701.912000] snd_rawmidi: disagrees about version of symbol snd_device_register
[4294701.912000] snd_rawmidi: Unknown symbol snd_device_register
[4294701.912000] snd_rawmidi: disagrees about version of symbol snd_register_device
[4294701.912000] snd_rawmidi: Unknown symbol snd_register_device
[4294701.937000] snd_emu10k1: Unknown symbol snd_rawmidi_receive
[4294701.937000] snd_emu10k1: Unknown symbol snd_rawmidi_transmit
[4294701.937000] snd_emu10k1: Unknown symbol snd_ac97_write_cache
[4294701.937000] snd_emu10k1: disagrees about version of symbol snd_ctl_add
[4294701.937000] snd_emu10k1: Unknown symbol snd_ctl_add
[4294701.937000] snd_emu10k1: Unknown symbol snd_ac97_resume
[4294701.937000] snd_emu10k1: disagrees about version of symbol snd_pcm_new
[4294701.938000] snd_emu10k1: Unknown symbol snd_pcm_new
[4294701.938000] snd_emu10k1: disagrees about version of symbol snd_seq_device_new
[4294701.938000] snd_emu10k1: Unknown symbol snd_seq_device_new
[4294701.938000] snd_emu10k1: disagrees about version of symbol snd_card_register
[4294701.938000] snd_emu10k1: Unknown symbol snd_card_register
[4294701.938000] snd_emu10k1: disagrees about version of symbol snd_card_free
[4294701.938000] snd_emu10k1: Unknown symbol snd_card_free
[4294701.938000] snd_emu10k1: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[4294701.938000] snd_emu10k1: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[4294701.938000] snd_emu10k1: disagrees about version of symbol snd_card_proc_new
[4294701.938000] snd_emu10k1: Unknown symbol snd_card_proc_new
[4294701.938000] snd_emu10k1: disagrees about version of symbol snd_pcm_hw_constraint_minmax
[4294701.938000] snd_emu10k1: Unknown symbol snd_pcm_hw_constraint_minmax
[4294701.938000] snd_emu10k1: disagrees about version of symbol snd_timer_interrupt
[4294701.938000] snd_emu10k1: Unknown symbol snd_timer_interrupt
[4294701.938000] snd_emu10k1: Unknown symbol snd_ac97_mixer
[4294701.938000] snd_emu10k1: disagrees about version of symbol snd_ctl_remove
[4294701.938000] snd_emu10k1: Unknown symbol snd_ctl_remove
[4294701.938000] snd_emu10k1: Unknown symbol snd_ac97_bus
[4294701.938000] snd_emu10k1: disagrees about version of symbol snd_ctl_find_id
[4294701.938000] snd_emu10k1: Unknown symbol snd_ctl_find_id
[4294701.938000] snd_emu10k1: disagrees about version of symbol snd_dma_free_pages
[4294701.938000] snd_emu10k1: Unknown symbol snd_dma_free_pages
[4294701.938000] snd_emu10k1: disagrees about version of symbol snd_ctl_new1
[4294701.938000] snd_emu10k1: Unknown symbol snd_ctl_new1
[4294701.938000] snd_emu10k1: disagrees about version of symbol snd_ctl_remove_id
[4294701.938000] snd_emu10k1: Unknown symbol snd_ctl_remove_id
[4294701.938000] snd_emu10k1: Unknown symbol snd_compat_kzalloc
[4294701.938000] snd_emu10k1: disagrees about version of symbol snd_card_new
[4294701.938000] snd_emu10k1: Unknown symbol snd_card_new
[4294701.938000] snd_emu10k1: Unknown symbol snd_ac97_suspend
[4294701.938000] snd_emu10k1: disagrees about version of symbol snd_iprintf
[4294701.938000] snd_emu10k1: Unknown symbol snd_iprintf
[4294701.938000] snd_emu10k1: disagrees about version of symbol snd_pcm_lib_malloc_pages
[4294701.938000] snd_emu10k1: Unknown symbol snd_pcm_lib_malloc_pages
[4294701.938000] snd_emu10k1: Unknown symbol __snd_util_mem_alloc
[4294701.938000] snd_emu10k1: Unknown symbol snd_util_memhdr_new
[4294701.938000] snd_emu10k1: disagrees about version of symbol snd_pcm_lib_ioctl
[4294701.938000] snd_emu10k1: Unknown symbol snd_pcm_lib_ioctl
[4294701.938000] snd_emu10k1: disagrees about version of symbol snd_pcm_lib_free_pages
[4294701.938000] snd_emu10k1: Unknown symbol snd_pcm_lib_free_pages
[4294701.938000] snd_emu10k1: Unknown symbol snd_hwdep_new
[4294701.938000] snd_emu10k1: disagrees about version of symbol snd_cards
[4294701.938000] snd_emu10k1: Unknown symbol snd_cards
[4294701.938000] snd_emu10k1: disagrees about version of symbol snd_ctl_notify
[4294701.938000] snd_emu10k1: Unknown symbol snd_ctl_notify
[4294701.938000] snd_emu10k1: disagrees about version of symbol snd_pcm_set_ops
[4294701.938000] snd_emu10k1: Unknown symbol snd_pcm_set_ops
[4294701.938000] snd_emu10k1: disagrees about version of symbol snd_timer_new
[4294701.938000] snd_emu10k1: Unknown symbol snd_timer_new
[4294701.938000] snd_emu10k1: disagrees about version of symbol snd_pcm_hw_constraint_list
[4294701.938000] snd_emu10k1: Unknown symbol snd_pcm_hw_constraint_list
[4294701.939000] snd_emu10k1: disagrees about version of symbol snd_device_new
[4294701.939000] snd_emu10k1: Unknown symbol snd_device_new
[4294701.939000] snd_emu10k1: disagrees about version of symbol snd_pcm_sgbuf_ops_page
[4294701.939000] snd_emu10k1: Unknown symbol snd_pcm_sgbuf_ops_page
[4294701.939000] snd_emu10k1: disagrees about version of symbol snd_pcm_suspend_all
[4294701.939000] snd_emu10k1: Unknown symbol snd_pcm_suspend_all
[4294701.939000] snd_emu10k1: Unknown symbol snd_rawmidi_new
[4294701.939000] snd_emu10k1: disagrees about version of symbol snd_pcm_hw_constraint_integer
[4294701.939000] snd_emu10k1: Unknown symbol snd_pcm_hw_constraint_integer
[4294701.939000] snd_emu10k1: Unknown symbol __snd_util_mem_free
[4294701.939000] snd_emu10k1: Unknown symbol snd_rawmidi_set_ops
[4294701.939000] snd_emu10k1: disagrees about version of symbol snd_pcm_lib_preallocate_pages
[4294701.939000] snd_emu10k1: Unknown symbol snd_pcm_lib_preallocate_pages
[4294701.939000] snd_emu10k1: Unknown symbol snd_util_memhdr_free
[4294701.939000] snd_emu10k1: disagrees about version of symbol snd_device_free
[4294701.939000] snd_emu10k1: Unknown symbol snd_device_free
[4294701.939000] snd_emu10k1: disagrees about version of symbol snd_dma_alloc_pages
[4294701.939000] snd_emu10k1: Unknown symbol snd_dma_alloc_pages
[4294701.939000] snd_emu10k1: disagrees about version of symbol snd_pcm_period_elapsed
[4294701.939000] snd_emu10k1: Unknown symbol snd_pcm_period_elapsed
[4294701.939000] snd_emu10k1: Unknown symbol __snd_util_memblk_new
[4294701.939000] snd_emu10k1: disagrees about version of symbol snd_pcm_format_width
[4294701.939000] snd_emu10k1: Unknown symbol snd_pcm_format_width

which doesn't look too good to me. 

Anyone got any suggestions on how to get this working?
Jeremy

---

### Post by Zeroedout on 2006-02-13
were their errors when you compiled? If so what were they? You can also try using another version of GCC, which may make it compile. From you're post though, it looks like it compiled and installed okay, however, (and I could be completly wrong), it looks to me as though it's just not recognizeing all parts of your sound card, though i would expect that in a development release.

---

### Post by mpvano on 2006-02-13
Did you compile it with gcc-3.40?

All kernel modules for breezy MUST be compiled with this compiler, which is the version the kernels themselves are compiled with.

Using the wrong version will give a successful build and install but the modules simply won't load and will display a variety of confusing errors.

If you are fairly sure you had no trouble building and installing the modules, all you may need to do is use apt-get to retrieve the correct compiler, temporarily replace the link that currently defines gcc as gcc-4.0 with the correct link for gcc-3.4. Build the driver from scratch again.

Don't forget to restore the link to pointing to 4.0, which is the correct compiler for breezy application programming!

I think that if you use install and use the package called module-assistant from the ubuntu repositories to install source packages, it will do this all for you automatically. I know it works for kernel modules I build, and I think I saw alsa in the list of things it knows how to build...

hope this helps,

Mario

---

### Post by jeremytaylor on 2006-02-13
Excellent, that might well be it. I'll give it a go. 
thanks!
Jeremy

---

