---
title: "no more sound"
date: 2008-09-26
forum: Multimedia Software
---

### Post by Zaff on 2008-09-26
Hi guys I tried installing OSS4 because the sound was of such a bad quality that I wanted to try somethign else but it didn't work. Now I tried to revert to ALSA but I can't get anything to work anymore.
My sound card won't get detected and modprobe snd-hda-intel returns this : 
```
FATAL: Error inserting snd (/lib/modules/2.6.24-19-generic/updates/alsa/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.24-19-generic/updates/alsa/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-19-generic/updates/alsa/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.24-19-generic/updates/alsa/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-19-generic/updates/alsa/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.24-19-generic/updates/alsa/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.24-19-generic/updates/alsa/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```
dmesg gives me this : 
```
[  372.266527] snd: Unknown symbol unregister_sound_special
[  372.266613] snd: Unknown symbol register_sound_special_device
[  372.266830] snd: Unknown symbol sound_class
[  372.286307] snd_hwdep: Unknown symbol snd_hidden_kzalloc
[  372.286342] snd_hwdep: Unknown symbol snd_info_register
[  372.286380] snd_hwdep: Unknown symbol snd_info_create_module_entry
[  372.286411] snd_hwdep: Unknown symbol snd_info_free_entry
[  372.286444] snd_hwdep: Unknown symbol snd_hidden_kfree
[  372.286475] snd_hwdep: Unknown symbol snd_unregister_oss_device
[  372.286509] snd_hwdep: Unknown symbol snd_verbose_printk
[  372.286540] snd_hwdep: Unknown symbol snd_register_oss_device
[  372.286573] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[  372.286604] snd_hwdep: Unknown symbol snd_card_file_add
[  372.286638] snd_hwdep: Unknown symbol snd_iprintf
[  372.286669] snd_hwdep: Unknown symbol snd_major
[  372.286721] snd_hwdep: Unknown symbol snd_unregister_device
[  372.286757] snd_hwdep: Unknown symbol snd_device_new
[  372.286789] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[  372.286826] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data
[  372.286859] snd_hwdep: Unknown symbol snd_lookup_minor_data
[  372.286892] snd_hwdep: Unknown symbol snd_card_file_remove
[  372.286923] snd_hwdep: Unknown symbol snd_register_device_for_dev
[  372.310300] snd_timer: Unknown symbol snd_verbose_printd
[  372.310336] snd_timer: Unknown symbol snd_hidden_kzalloc
[  372.310367] snd_timer: Unknown symbol snd_info_register
[  372.310405] snd_timer: Unknown symbol snd_info_create_module_entry
[  372.310441] snd_timer: Unknown symbol snd_info_free_entry
[  372.310476] snd_timer: Unknown symbol snd_hidden_kfree
[  372.310526] snd_timer: Unknown symbol snd_verbose_printk
[  372.310562] snd_timer: Unknown symbol snd_iprintf
[  372.310606] snd_timer: Unknown symbol snd_ecards_limit
[  372.310647] snd_timer: Unknown symbol snd_oss_info_register
[  372.310678] snd_timer: Unknown symbol snd_unregister_device
[  372.310714] snd_timer: Unknown symbol snd_hidden_kstrdup
[  372.310745] snd_timer: Unknown symbol snd_device_new
[  372.310805] snd_timer: Unknown symbol snd_hidden_kmalloc
[  372.310836] snd_timer: Unknown symbol snd_register_device_for_dev
[  372.323170] snd: Unknown symbol unregister_sound_special
[  372.323261] snd: Unknown symbol register_sound_special_device
[  372.323485] snd: Unknown symbol sound_class
[  372.326183] snd_timer: Unknown symbol snd_verbose_printd
[  372.326221] snd_timer: Unknown symbol snd_hidden_kzalloc
[  372.326251] snd_timer: Unknown symbol snd_info_register
[  372.326288] snd_timer: Unknown symbol snd_info_create_module_entry
[  372.326323] snd_timer: Unknown symbol snd_info_free_entry
[  372.326357] snd_timer: Unknown symbol snd_hidden_kfree
[  372.326405] snd_timer: Unknown symbol snd_verbose_printk
[  372.326441] snd_timer: Unknown symbol snd_iprintf
[  372.326482] snd_timer: Unknown symbol snd_ecards_limit
[  372.326522] snd_timer: Unknown symbol snd_oss_info_register
[  372.326570] snd_timer: Unknown symbol snd_unregister_device
[  372.326606] snd_timer: Unknown symbol snd_hidden_kstrdup
[  372.326636] snd_timer: Unknown symbol snd_device_new
[  372.326695] snd_timer: Unknown symbol snd_hidden_kmalloc
[  372.326725] snd_timer: Unknown symbol snd_register_device_for_dev
[  372.393447] snd_pcm: Unknown symbol snd_verbose_printd
[  372.393485] snd_pcm: Unknown symbol snd_hidden_kzalloc
[  372.393517] snd_pcm: Unknown symbol snd_info_register
[  372.393556] snd_pcm: Unknown symbol snd_info_create_module_entry
[  372.393610] snd_pcm: Unknown symbol snd_timer_notify
[  372.393650] snd_pcm: Unknown symbol snd_timer_interrupt
[  372.393682] snd_pcm: Unknown symbol snd_info_free_entry
[  372.393714] snd_pcm: Unknown symbol snd_add_device_sysfs_file
[  372.393750] snd_pcm: Unknown symbol snd_info_get_str
[  372.393782] snd_pcm: Unknown symbol snd_hidden_kcalloc
[  372.393818] snd_pcm: Unknown symbol snd_hidden_kfree
[  372.393886] snd_pcm: Unknown symbol snd_verbose_printk
[  372.393948] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[  372.393981] snd_pcm: Unknown symbol snd_card_file_add
[  372.394017] snd_pcm: Unknown symbol snd_iprintf
[  372.394064] snd_pcm: Unknown symbol snd_major
[  372.394133] snd_pcm: Unknown symbol snd_unregister_device
[  372.394169] snd_pcm: Unknown symbol snd_timer_new
[  372.394202] snd_pcm: Unknown symbol snd_device_new
[  372.394254] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[  372.394301] snd_pcm: Unknown symbol snd_lookup_minor_data
[  372.394343] snd_pcm: Unknown symbol snd_info_create_card_entry
[  372.394375] snd_pcm: Unknown symbol snd_power_wait
[  372.394410] snd_pcm: Unknown symbol snd_hidden_kmalloc
[  372.394442] snd_pcm: Unknown symbol snd_device_free
[  372.394493] snd_pcm: Unknown symbol snd_card_file_remove
[  372.394539] snd_pcm: Unknown symbol snd_register_device_for_dev
[  372.394608] snd_pcm: Unknown symbol snd_device_register
[  372.394642] snd_pcm: Unknown symbol snd_info_get_line
[  372.444804] snd_hda_intel: Unknown symbol snd_verbose_printd
[  372.444840] snd_hda_intel: Unknown symbol snd_hidden_kzalloc
[  372.444889] snd_hda_intel: Unknown symbol snd_ctl_add
[  372.444936] snd_hda_intel: Unknown symbol snd_pcm_new
[  372.444974] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[  372.445009] snd_hda_intel: Unknown symbol snd_card_register
[  372.445040] snd_hda_intel: Unknown symbol snd_card_free
[  372.445071] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  372.445102] snd_hda_intel: Unknown symbol snd_card_proc_new
[  372.445168] snd_hda_intel: Unknown symbol snd_hidden_kcalloc
[  372.445208] snd_hda_intel: Unknown symbol snd_hidden_kfree
[  372.445254] snd_hda_intel: Unknown symbol snd_ctl_find_id
[  372.445293] snd_hda_intel: Unknown symbol snd_verbose_printk
[  372.445345] snd_hda_intel: Unknown symbol snd_ctl_new1
[  372.445408] snd_hda_intel: Unknown symbol snd_component_add
[  372.445442] snd_hda_intel: Unknown symbol snd_card_new
[  372.445473] snd_hda_intel: Unknown symbol snd_iprintf
[  372.445507] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[  372.445538] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info
[  372.445578] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[  372.445612] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[  372.445643] snd_hda_intel: Unknown symbol snd_hwdep_new
[  372.445686] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[  372.445724] snd_hda_intel: Unknown symbol snd_hidden_kstrdup
[  372.445755] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[  372.445805] snd_hda_intel: Unknown symbol snd_device_new
[  372.445836] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_ops_page
[  372.445881] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[  372.445920] snd_hda_intel: Unknown symbol snd_card_disconnect
[  372.445951] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[  372.446019] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[  372.446063] snd_hda_intel: Unknown symbol snd_hidden_kmalloc
[  372.446113] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[  372.446144] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[  372.446186] snd_hda_intel: Unknown symbol snd_pcm_format_width

```
I really need some help on this I'm going crazy please...

---

### Post by Zaff on 2008-09-27
okay nevermind, the issue came from the module soundcore being deleted. So I reinstalled the linux image but it seems something in OSS4 was still there deleting it at boot or shutdown so I eventually just reinstalled Ubuntu entirely, which I would eventually have done anyway seeing as I was getting a lot of issues from various tweaking.
So here it is.

---

