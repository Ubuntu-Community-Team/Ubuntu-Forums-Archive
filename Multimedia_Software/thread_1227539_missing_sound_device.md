---
title: "missing sound device"
date: 2009-07-30
forum: Multimedia Software
---

### Post by shmish on 2009-07-30
Hello,
Ubuntu doesn't seem to be detecting my sound device.
aplay -l says there aren't any devices.
lspci -v shows the sound device ( an Intel Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller)

I've read some troubleshooting guides but it is hard for me to tell what is current and works for 8.10.  For instance, one guide asks to run:

```
sudo modprobe -snd
```

and when I do this I get
```
module snd_ not found
```

I have ALSA and Pulseaudio installed and things used to work.  I had added an echo audio card and had it working somewhat.  After removing the echo card, the built-in audio card stopped being recognized.

Thanks for your help.

---

### Post by shmish on 2009-07-30
I found a bunch of log messages that might shed some light.  First, the built-in audio:
```
Jul 30 16:59:48 ubuntu kernel: [   17.344154] snd_ac97_codec: Unknown symbol snd_ctl_add_slave
Jul 30 16:59:48 ubuntu kernel: [   17.344263] snd_ac97_codec: disagrees about version of symbol snd_info_register
Jul 30 16:59:48 ubuntu kernel: [   17.344266] snd_ac97_codec: Unknown symbol snd_info_register
Jul 30 16:59:48 ubuntu kernel: [   17.344371] snd_ac97_codec: disagrees about version of symbol snd_ctl_add
Jul 30 16:59:48 ubuntu kernel: [   17.344374] snd_ac97_codec: Unknown symbol snd_ctl_add
Jul 30 16:59:48 ubuntu kernel: [   17.344606] snd_ac97_codec: disagrees about version of symbol snd_info_free_entry
Jul 30 16:59:48 ubuntu kernel: [   17.344608] snd_ac97_codec: Unknown symbol snd_info_free_entry
Jul 30 16:59:48 ubuntu kernel: [   17.344841] snd_ac97_codec: disagrees about version of symbol snd_ctl_find_id
Jul 30 16:59:48 ubuntu kernel: [   17.344844] snd_ac97_codec: Unknown symbol snd_ctl_find_id
Jul 30 16:59:48 ubuntu kernel: [   17.344949] snd_ac97_codec: disagrees about version of symbol snd_ctl_new1
Jul 30 16:59:48 ubuntu kernel: [   17.344951] snd_ac97_codec: Unknown symbol snd_ctl_new1
Jul 30 16:59:48 ubuntu kernel: [   17.345070] snd_ac97_codec: disagrees about version of symbol snd_ctl_remove_id
Jul 30 16:59:48 ubuntu kernel: [   17.345073] snd_ac97_codec: Unknown symbol snd_ctl_remove_id
Jul 30 16:59:48 ubuntu kernel: [   17.345216] snd_ac97_codec: disagrees about version of symbol snd_component_add
Jul 30 16:59:48 ubuntu kernel: [   17.345218] snd_ac97_codec: Unknown symbol snd_component_add
Jul 30 16:59:48 ubuntu kernel: [   17.345343] snd_ac97_codec: Unknown symbol snd_ctl_make_virtual_master
Jul 30 16:59:48 ubuntu kernel: [   17.345441] snd_ac97_codec: disagrees about version of symbol snd_pcm_hw_rule_add
Jul 30 16:59:48 ubuntu kernel: [   17.345444] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
Jul 30 16:59:48 ubuntu kernel: [   17.345707] snd_ac97_codec: disagrees about version of symbol snd_ctl_boolean_mono_info
Jul 30 16:59:48 ubuntu kernel: [   17.345710] snd_ac97_codec: Unknown symbol snd_ctl_boolean_mono_info
Jul 30 16:59:48 ubuntu kernel: [   17.346033] snd_ac97_codec: disagrees about version of symbol snd_device_new
Jul 30 16:59:48 ubuntu kernel: [   17.346036] snd_ac97_codec: Unknown symbol snd_device_new
Jul 30 16:59:48 ubuntu kernel: [   17.346308] snd_ac97_codec: disagrees about version of symbol snd_info_create_card_entry
Jul 30 16:59:48 ubuntu kernel: [   17.346311] snd_ac97_codec: Unknown symbol snd_info_create_card_entry
Jul 30 16:59:48 ubuntu kernel: [   17.366008] snd_intel8x0: Unknown symbol snd_ac97_pcm_close
Jul 30 16:59:48 ubuntu kernel: [   17.366251] snd_intel8x0: Unknown symbol snd_ac97_resume
Jul 30 16:59:48 ubuntu kernel: [   17.366349] snd_intel8x0: disagrees about version of symbol snd_pcm_new
Jul 30 16:59:48 ubuntu kernel: [   17.366352] snd_intel8x0: Unknown symbol snd_pcm_new
Jul 30 16:59:48 ubuntu kernel: [   17.366486] snd_intel8x0: disagrees about version of symbol snd_pcm_limit_hw_rates
Jul 30 16:59:48 ubuntu kernel: [   17.366489] snd_intel8x0: Unknown symbol snd_pcm_limit_hw_rates
Jul 30 16:59:48 ubuntu kernel: [   17.366604] snd_intel8x0: disagrees about version of symbol snd_card_register
Jul 30 16:59:48 ubuntu kernel: [   17.366607] snd_intel8x0: Unknown symbol snd_card_register
Jul 30 16:59:48 ubuntu kernel: [   17.366711] snd_intel8x0: disagrees about version of symbol snd_card_free
Jul 30 16:59:48 ubuntu kernel: [   17.366714] snd_intel8x0: Unknown symbol snd_card_free
Jul 30 16:59:48 ubuntu kernel: [   17.366814] snd_intel8x0: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
Jul 30 16:59:48 ubuntu kernel: [   17.366817] snd_intel8x0: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
Jul 30 16:59:48 ubuntu kernel: [   17.366922] snd_intel8x0: disagrees about version of symbol snd_card_proc_new
Jul 30 16:59:48 ubuntu kernel: [   17.366925] snd_intel8x0: Unknown symbol snd_card_proc_new
Jul 30 16:59:48 ubuntu kernel: [   17.367090] snd_intel8x0: Unknown symbol snd_ac97_pcm_open
Jul 30 16:59:48 ubuntu kernel: [   17.367350] snd_intel8x0: Unknown symbol snd_ac97_set_rate
Jul 30 16:59:48 ubuntu kernel: [   17.367473] snd_intel8x0: Unknown symbol snd_ac97_update_bits
Jul 30 16:59:48 ubuntu kernel: [   17.367608] snd_intel8x0: Unknown symbol snd_ac97_mixer
Jul 30 16:59:48 ubuntu kernel: [   17.367786] snd_intel8x0: Unknown symbol snd_ac97_bus
Jul 30 16:59:48 ubuntu kernel: [   17.368162] snd_intel8x0: Unknown symbol snd_ac97_pcm_double_rate_rules
Jul 30 16:59:48 ubuntu kernel: [   17.368306] snd_intel8x0: Unknown symbol snd_ac97_update_power
Jul 30 16:59:48 ubuntu kernel: [   17.368430] snd_intel8x0: Unknown symbol snd_card_new
Jul 30 16:59:48 ubuntu kernel: [   17.368553] snd_intel8x0: Unknown symbol snd_ac97_suspend
Jul 30 16:59:48 ubuntu kernel: [   17.368769] snd_intel8x0: disagrees about version of symbol snd_pcm_lib_malloc_pages
Jul 30 16:59:48 ubuntu kernel: [   17.368772] snd_intel8x0: Unknown symbol snd_pcm_lib_malloc_pages
Jul 30 16:59:48 ubuntu kernel: [   17.368869] snd_intel8x0: disagrees about version of symbol snd_pcm_lib_ioctl
Jul 30 16:59:48 ubuntu kernel: [   17.368872] snd_intel8x0: Unknown symbol snd_pcm_lib_ioctl
Jul 30 16:59:48 ubuntu kernel: [   17.368981] snd_intel8x0: disagrees about version of symbol snd_pcm_lib_free_pages
Jul 30 16:59:48 ubuntu kernel: [   17.368984] snd_intel8x0: Unknown symbol snd_pcm_lib_free_pages
Jul 30 16:59:48 ubuntu kernel: [   17.369132] snd_intel8x0: disagrees about version of symbol snd_pcm_set_ops
Jul 30 16:59:48 ubuntu kernel: [   17.369134] snd_intel8x0: Unknown symbol snd_pcm_set_ops
Jul 30 16:59:48 ubuntu kernel: [   17.369249] snd_intel8x0: disagrees about version of symbol snd_pcm_hw_constraint_list
Jul 30 16:59:48 ubuntu kernel: [   17.369252] snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_list
Jul 30 16:59:48 ubuntu kernel: [   17.369469] snd_intel8x0: disagrees about version of symbol snd_device_new
Jul 30 16:59:48 ubuntu kernel: [   17.369472] snd_intel8x0: Unknown symbol snd_device_new
Jul 30 16:59:48 ubuntu kernel: [   17.369645] snd_intel8x0: Unknown symbol snd_ac97_get_short_name
Jul 30 16:59:48 ubuntu kernel: [   17.369741] snd_intel8x0: disagrees about version of symbol snd_pcm_suspend_all
Jul 30 16:59:48 ubuntu kernel: [   17.369743] snd_intel8x0: Unknown symbol snd_pcm_suspend_all
Jul 30 16:59:48 ubuntu kernel: [   17.369852] snd_intel8x0: disagrees about version of symbol snd_card_disconnect
Jul 30 16:59:48 ubuntu kernel: [   17.369854] snd_intel8x0: Unknown symbol snd_card_disconnect
Jul 30 16:59:48 ubuntu kernel: [   17.369978] snd_intel8x0: Unknown symbol snd_ac97_pcm_assign
Jul 30 16:59:48 ubuntu kernel: [   17.370075] snd_intel8x0: disagrees about version of symbol snd_pcm_hw_constraint_integer
Jul 30 16:59:48 ubuntu kernel: [   17.370078] snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_integer
Jul 30 16:59:48 ubuntu kernel: [   17.370312] snd_intel8x0: disagrees about version of symbol snd_pci_quirk_lookup
Jul 30 16:59:48 ubuntu kernel: [   17.370315] snd_intel8x0: Unknown symbol snd_pci_quirk_lookup
Jul 30 16:59:48 ubuntu kernel: [   17.370462] snd_intel8x0: disagrees about version of symbol snd_pcm_hw_constraint_msbits
Jul 30 16:59:48 ubuntu kernel: [   17.370465] snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_msbits
Jul 30 16:59:48 ubuntu kernel: [   17.370663] snd_intel8x0: disagrees about version of symbol snd_pcm_period_elapsed
Jul 30 16:59:48 ubuntu kernel: [   17.370666] snd_intel8x0: Unknown symbol snd_pcm_period_elapsed
Jul 30 16:59:48 ubuntu kernel: [   17.370796] snd_intel8x0: Unknown symbol snd_ac97_tune_hardware
```

And also the echo indigo DJ audio card:
```
Jul 30 16:59:48 ubuntu kernel: [   20.164701] snd_indigodj: disagrees about version of symbol snd_ctl_add
Jul 30 16:59:48 ubuntu kernel: [   20.164706] snd_indigodj: Unknown symbol snd_ctl_add
Jul 30 16:59:48 ubuntu kernel: [   20.164841] snd_indigodj: disagrees about version of symbol snd_pcm_new
Jul 30 16:59:48 ubuntu kernel: [   20.164844] snd_indigodj: Unknown symbol snd_pcm_new
Jul 30 16:59:48 ubuntu kernel: [   20.164961] snd_indigodj: disagrees about version of symbol snd_card_register
Jul 30 16:59:48 ubuntu kernel: [   20.164964] snd_indigodj: Unknown symbol snd_card_register
Jul 30 16:59:48 ubuntu kernel: [   20.165071] snd_indigodj: disagrees about version of symbol snd_card_free
Jul 30 16:59:48 ubuntu kernel: [   20.165073] snd_indigodj: Unknown symbol snd_card_free
Jul 30 16:59:48 ubuntu kernel: [   20.165532] snd_indigodj: disagrees about version of symbol snd_pcm_set_sync
Jul 30 16:59:48 ubuntu kernel: [   20.165534] snd_indigodj: Unknown symbol snd_pcm_set_sync
Jul 30 16:59:48 ubuntu kernel: [   20.165792] snd_indigodj: disagrees about version of symbol snd_ctl_new1
Jul 30 16:59:48 ubuntu kernel: [   20.165795] snd_indigodj: Unknown symbol snd_ctl_new1
Jul 30 16:59:48 ubuntu kernel: [   20.165911] snd_indigodj: disagrees about version of symbol snd_pcm_hw_rule_add
Jul 30 16:59:48 ubuntu kernel: [   20.165914] snd_indigodj: Unknown symbol snd_pcm_hw_rule_add
Jul 30 16:59:48 ubuntu kernel: [   20.166056] snd_indigodj: Unknown symbol snd_card_new
Jul 30 16:59:48 ubuntu kernel: [   20.166158] snd_indigodj: disagrees about version of symbol snd_pcm_lib_malloc_pages
Jul 30 16:59:48 ubuntu kernel: [   20.166161] snd_indigodj: Unknown symbol snd_pcm_lib_malloc_pages
Jul 30 16:59:48 ubuntu kernel: [   20.166269] snd_indigodj: disagrees about version of symbol snd_ctl_boolean_mono_info
Jul 30 16:59:48 ubuntu kernel: [   20.166272] snd_indigodj: Unknown symbol snd_ctl_boolean_mono_info
Jul 30 16:59:48 ubuntu kernel: [   20.166372] snd_indigodj: disagrees about version of symbol snd_pcm_lib_ioctl
Jul 30 16:59:48 ubuntu kernel: [   20.166375] snd_indigodj: Unknown symbol snd_pcm_lib_ioctl
Jul 30 16:59:48 ubuntu kernel: [   20.166580] snd_indigodj: disagrees about version of symbol snd_pcm_lib_free_pages
Jul 30 16:59:48 ubuntu kernel: [   20.166583] snd_indigodj: Unknown symbol snd_pcm_lib_free_pages
Jul 30 16:59:48 ubuntu kernel: [   20.166698] snd_indigodj: disagrees about version of symbol snd_pcm_set_ops
Jul 30 16:59:48 ubuntu kernel: [   20.166701] snd_indigodj: Unknown symbol snd_pcm_set_ops
Jul 30 16:59:48 ubuntu kernel: [   20.166828] snd_indigodj: disagrees about version of symbol snd_pcm_hw_constraint_list
Jul 30 16:59:48 ubuntu kernel: [   20.166831] snd_indigodj: Unknown symbol snd_pcm_hw_constraint_list
Jul 30 16:59:48 ubuntu kernel: [   20.166938] snd_indigodj: disagrees about version of symbol snd_device_new
Jul 30 16:59:48 ubuntu kernel: [   20.166941] snd_indigodj: Unknown symbol snd_device_new
Jul 30 16:59:48 ubuntu kernel: [   20.167042] snd_indigodj: disagrees about version of symbol snd_pcm_sgbuf_ops_page
Jul 30 16:59:48 ubuntu kernel: [   20.167045] snd_indigodj: Unknown symbol snd_pcm_sgbuf_ops_page
Jul 30 16:59:48 ubuntu kernel: [   20.167195] snd_indigodj: disagrees about version of symbol snd_pcm_hw_constraint_integer
Jul 30 16:59:48 ubuntu kernel: [   20.167198] snd_indigodj: Unknown symbol snd_pcm_hw_constraint_integer
Jul 30 16:59:48 ubuntu kernel: [   20.167351] snd_indigodj: disagrees about version of symbol snd_pcm_lib_preallocate_pages
Jul 30 16:59:48 ubuntu kernel: [   20.167354] snd_indigodj: Unknown symbol snd_pcm_lib_preallocate_pages
Jul 30 16:59:48 ubuntu kernel: [   20.167653] snd_indigodj: disagrees about version of symbol snd_pcm_period_elapsed
Jul 30 16:59:48 ubuntu kernel: [   20.167655] snd_indigodj: Unknown symbol snd_pcm_period_elapsed
Jul 30 16:59:48 ubuntu kernel: [   20.167755] snd_indigodj: disagrees about version of symbol snd_pcm_hw_constraint_step
Jul 30 16:59:48 ubuntu kernel: [   20.167758] snd_indigodj: Unknown symbol snd_pcm_hw_constraint_step
```

---

