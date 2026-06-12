---
title: "Sound not working all of a sudden, 8.04"
date: 2008-11-04
forum: Multimedia Software
---

### Post by LokeTheDog on 2008-11-04
"aplay -l" gives:

kort 1: snd_ctl_card_info_get_id [Intel HD Audio], enhet 0: OSS ID [HD Audio front]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: OSS subname
kort 1: snd_ctl_card_info_get_id [Intel HD Audio], enhet 1: OSS ID [HD Audio rear]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: OSS subname
kort 1: snd_ctl_card_info_get_id [Intel HD Audio], enhet 2: OSS ID [HD Audio center/LFE]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: OSS subname
kort 1: snd_ctl_card_info_get_id [Intel HD Audio], enhet 3: OSS ID [HD Audio side]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: OSS subname
kort 1: snd_ctl_card_info_get_id [Intel HD Audio], enhet 4: OSS ID [HD Audio pcm4]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: OSS subname
kort 1: snd_ctl_card_info_get_id [Intel HD Audio], enhet 5: OSS ID [HD Audio spdif-out]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: OSS subname
kort 1: snd_ctl_card_info_get_id [Intel HD Audio], enhet 6: OSS ID [High Definition Audio rec]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: OSS subname
kort 1: snd_ctl_card_info_get_id [Intel HD Audio], enhet 7: OSS ID [High Definition Audio rec1]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: OSS subname
kort 1: snd_ctl_card_info_get_id [Intel HD Audio], enhet 8: OSS ID [High Definition Audio rec2]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: OSS subname
kort 1: snd_ctl_card_info_get_id [Intel HD Audio], enhet 9: OSS ID [High Definition Audio spdif-in]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: OSS subname


That's swedish, yes, but I'm sure anyone who understands this stuff will still get it. Anyway, no problems there as far as I can tell.

"alsamixer" gives:

snd_mixer_set_callback()
No mixer elems found

And in "/var/log/messages" i find:

```
Nov  4 19:19:05 martins kernel: [   60.557362] snd: Unknown symbol unregister_sound_special
Nov  4 19:19:05 martins kernel: [   60.557438] snd: Unknown symbol register_sound_special_device
Nov  4 19:19:05 martins kernel: [   60.557648] snd: Unknown symbol sound_class
Nov  4 19:19:05 martins kernel: [   60.568640] snd_hwdep: Unknown symbol snd_info_register
Nov  4 19:19:05 martins kernel: [   60.568662] snd_hwdep: Unknown symbol snd_info_create_module_entry
Nov  4 19:19:05 martins kernel: [   60.568683] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl_compat
Nov  4 19:19:05 martins kernel: [   60.568704] snd_hwdep: Unknown symbol snd_info_free_entry
Nov  4 19:19:05 martins kernel: [   60.568729] snd_hwdep: Unknown symbol snd_unregister_oss_device
Nov  4 19:19:05 martins kernel: [   60.568753] snd_hwdep: Unknown symbol snd_verbose_printk
Nov  4 19:19:05 martins kernel: [   60.568774] snd_hwdep: Unknown symbol snd_register_oss_device
Nov  4 19:19:05 martins kernel: [   60.568796] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
Nov  4 19:19:05 martins kernel: [   60.568817] snd_hwdep: Unknown symbol snd_card_file_add
Nov  4 19:19:05 martins kernel: [   60.568843] snd_hwdep: Unknown symbol snd_iprintf
Nov  4 19:19:05 martins kernel: [   60.568863] snd_hwdep: Unknown symbol snd_major
Nov  4 19:19:05 martins kernel: [   60.568892] snd_hwdep: Unknown symbol snd_unregister_device
Nov  4 19:19:05 martins kernel: [   60.568915] snd_hwdep: Unknown symbol snd_device_new
Nov  4 19:19:05 martins kernel: [   60.568943] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
Nov  4 19:19:05 martins kernel: [   60.568970] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data
Nov  4 19:19:05 martins kernel: [   60.568992] snd_hwdep: Unknown symbol snd_lookup_minor_data
Nov  4 19:19:05 martins kernel: [   60.569013] snd_hwdep: Unknown symbol snd_ctl_register_ioctl_compat
Nov  4 19:19:05 martins kernel: [   60.569036] snd_hwdep: Unknown symbol snd_card_file_remove
Nov  4 19:19:05 martins kernel: [   60.569056] snd_hwdep: Unknown symbol snd_register_device_for_dev
Nov  4 19:19:05 martins kernel: [   60.587823] snd_timer: Unknown symbol snd_info_register
Nov  4 19:19:05 martins kernel: [   60.587846] snd_timer: Unknown symbol snd_info_create_module_entry
Nov  4 19:19:05 martins kernel: [   60.587871] snd_timer: Unknown symbol snd_info_free_entry
Nov  4 19:19:05 martins kernel: [   60.587913] snd_timer: Unknown symbol snd_verbose_printk
Nov  4 19:19:05 martins kernel: [   60.587941] snd_timer: Unknown symbol snd_iprintf
Nov  4 19:19:05 martins kernel: [   60.587973] snd_timer: Unknown symbol snd_ecards_limit
Nov  4 19:19:05 martins kernel: [   60.587997] snd_timer: Unknown symbol snd_oss_info_register
Nov  4 19:19:05 martins kernel: [   60.588018] snd_timer: Unknown symbol snd_unregister_device
Nov  4 19:19:05 martins kernel: [   60.588044] snd_timer: Unknown symbol snd_device_new
Nov  4 19:19:05 martins kernel: [   60.588102] snd_timer: Unknown symbol snd_register_device_for_dev
Nov  4 19:19:05 martins kernel: [   60.592503] snd: Unknown symbol unregister_sound_special
Nov  4 19:19:05 martins kernel: [   60.592578] snd: Unknown symbol register_sound_special_device
Nov  4 19:19:05 martins kernel: [   60.592790] snd: Unknown symbol sound_class
Nov  4 19:19:05 martins kernel: [   60.656254] snd_timer: Unknown symbol snd_info_register
Nov  4 19:19:05 martins kernel: [   60.656277] snd_timer: Unknown symbol snd_info_create_module_entry
Nov  4 19:19:05 martins kernel: [   60.656301] snd_timer: Unknown symbol snd_info_free_entry
Nov  4 19:19:05 martins kernel: [   60.656344] snd_timer: Unknown symbol snd_verbose_printk
Nov  4 19:19:05 martins kernel: [   60.656371] snd_timer: Unknown symbol snd_iprintf
Nov  4 19:19:05 martins kernel: [   60.656403] snd_timer: Unknown symbol snd_ecards_limit
Nov  4 19:19:05 martins kernel: [   60.656428] snd_timer: Unknown symbol snd_oss_info_register
Nov  4 19:19:05 martins kernel: [   60.656449] snd_timer: Unknown symbol snd_unregister_device
Nov  4 19:19:05 martins kernel: [   60.656474] snd_timer: Unknown symbol snd_device_new
Nov  4 19:19:05 martins kernel: [   60.656500] ACPI: Power Button (FF) [PWRF]
Nov  4 19:19:05 martins kernel: [   60.656526] snd_timer: Unknown symbol snd_register_device_for_dev
Nov  4 19:19:05 martins kernel: [   60.656539] input: Power Button (CM) as /devices/virtual/input/input6
Nov  4 19:19:05 martins kernel: [   60.661209] snd_pcm: Unknown symbol snd_info_register
Nov  4 19:19:05 martins kernel: [   60.661232] snd_pcm: Unknown symbol snd_info_create_module_entry
Nov  4 19:19:05 martins kernel: [   60.661253] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl_compat
Nov  4 19:19:05 martins kernel: [   60.661294] snd_pcm: Unknown symbol snd_timer_notify
Nov  4 19:19:05 martins kernel: [   60.661321] snd_pcm: Unknown symbol snd_timer_interrupt
Nov  4 19:19:05 martins kernel: [   60.661342] snd_pcm: Unknown symbol snd_info_free_entry
Nov  4 19:19:05 martins kernel: [   60.661363] snd_pcm: Unknown symbol snd_add_device_sysfs_file
Nov  4 19:19:05 martins kernel: [   60.661391] snd_pcm: Unknown symbol snd_info_get_str
Nov  4 19:19:05 martins kernel: [   60.661446] snd_pcm: Unknown symbol snd_verbose_printk
Nov  4 19:19:05 martins kernel: [   60.661494] snd_pcm: Unknown symbol snd_ctl_register_ioctl
Nov  4 19:19:05 martins kernel: [   60.661515] snd_pcm: Unknown symbol snd_card_file_add
Nov  4 19:19:05 martins kernel: [   60.661541] snd_pcm: Unknown symbol snd_iprintf
Nov  4 19:19:05 martins kernel: [   60.661576] snd_pcm: Unknown symbol snd_major
Nov  4 19:19:05 martins kernel: [   60.661625] snd_pcm: Unknown symbol snd_unregister_device
Nov  4 19:19:05 martins kernel: [   60.661650] snd_pcm: Unknown symbol snd_timer_new
Nov  4 19:19:05 martins kernel: [   60.661670] snd_pcm: Unknown symbol snd_device_new
Nov  4 19:19:05 martins kernel: [   60.661712] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
Nov  4 19:19:05 martins kernel: [   60.661748] snd_pcm: Unknown symbol snd_lookup_minor_data
Nov  4 19:19:05 martins kernel: [   60.661768] snd_pcm: Unknown symbol snd_ctl_register_ioctl_compat
Nov  4 19:19:05 martins kernel: [   60.661798] snd_pcm: Unknown symbol snd_info_create_card_entry
Nov  4 19:19:05 martins kernel: [   60.661819] snd_pcm: Unknown symbol snd_power_wait
Nov  4 19:19:05 martins kernel: [   60.661843] snd_pcm: Unknown symbol snd_device_free
Nov  4 19:19:05 martins kernel: [   60.661880] snd_pcm: Unknown symbol snd_card_file_remove
Nov  4 19:19:05 martins kernel: [   60.661901] snd_pcm: Unknown symbol snd_register_device_for_dev
Nov  4 19:19:05 martins kernel: [   60.661953] snd_pcm: Unknown symbol snd_device_register
Nov  4 19:19:05 martins kernel: [   60.661975] snd_pcm: Unknown symbol snd_info_get_line
Nov  4 19:19:05 martins kernel: [   60.686827] snd_hda_intel: Unknown symbol snd_ctl_add
Nov  4 19:19:05 martins kernel: [   60.686858] snd_hda_intel: Unknown symbol snd_pcm_new
Nov  4 19:19:05 martins kernel: [   60.686886] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
Nov  4 19:19:05 martins kernel: [   60.686910] snd_hda_intel: Unknown symbol snd_card_register
Nov  4 19:19:05 martins kernel: [   60.686931] snd_hda_intel: Unknown symbol snd_card_free
Nov  4 19:19:05 martins kernel: [   60.686952] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
Nov  4 19:19:05 martins kernel: [   60.686973] snd_hda_intel: Unknown symbol snd_card_proc_new
Nov  4 19:19:05 martins kernel: [   60.687046] snd_hda_intel: Unknown symbol snd_ctl_find_id
Nov  4 19:19:05 martins kernel: [   60.687074] snd_hda_intel: Unknown symbol snd_verbose_printk
Nov  4 19:19:05 martins kernel: [   60.687112] snd_hda_intel: Unknown symbol snd_ctl_new1
Nov  4 19:19:05 martins kernel: [   60.687160] snd_hda_intel: Unknown symbol snd_component_add
Nov  4 19:19:05 martins kernel: [   60.687187] snd_hda_intel: Unknown symbol snd_card_new
Nov  4 19:19:05 martins kernel: [   60.687208] snd_hda_intel: Unknown symbol snd_iprintf
Nov  4 19:19:05 martins kernel: [   60.687231] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
Nov  4 19:19:05 martins kernel: [   60.687252] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info
Nov  4 19:19:05 martins kernel: [   60.687281] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
Nov  4 19:19:05 martins kernel: [   60.687305] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
Nov  4 19:19:05 martins kernel: [   60.687325] snd_hda_intel: Unknown symbol snd_hwdep_new
Nov  4 19:19:05 martins kernel: [   60.687350] snd_hda_intel: Unknown symbol snd_pcm_set_ops
Nov  4 19:19:05 martins kernel: [   60.687377] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
Nov  4 19:19:05 martins kernel: [   60.687405] snd_hda_intel: Unknown symbol snd_device_new
Nov  4 19:19:05 martins kernel: [   60.687439] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
Nov  4 19:19:05 martins kernel: [   60.687469] snd_hda_intel: Unknown symbol snd_card_disconnect
Nov  4 19:19:05 martins kernel: [   60.687490] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
Nov  4 19:19:05 martins kernel: [   60.687547] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
Nov  4 19:19:05 martins kernel: [   60.687596] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
Nov  4 19:19:05 martins kernel: [   60.687617] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
Nov  4 19:19:05 martins kernel: [   60.687653] snd_hda_intel: Unknown symbol snd_pcm_format_width
```

So something seems to go wrong there. Any idea what I can do about it? As a side note, I have no idea what screwed this up, it happened after a reboot, and I can't really remember what I did since I last rebooted.

---

### Post by LokeTheDog on 2008-11-05
Hmm, no replies? Is there something I should add to get help?

---

