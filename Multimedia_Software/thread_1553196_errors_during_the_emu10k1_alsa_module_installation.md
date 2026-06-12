---
title: "errors during the emu10k1 alsa module installation"
date: 2010-08-14
forum: Multimedia Software
---

### Post by gogitosbanditos on 2010-08-14
after trying to insert the modules into the kernel (executing the following:     ```
modprobe snd-emu10k1 ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
``` )
, several fatal errors happen:

```
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.32-24-generic/updates/alsa/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_emu10k1 (/lib/modules/2.6.32-24-generic/updates/alsa/snd-emu10k1.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.32-24-generic/updates/alsa/snd-page-alloc.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.32-24-generic/updates/alsa/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_pcm (/lib/modules/2.6.32-24-generic/updates/alsa/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm_oss (/lib/modules/2.6.32-24-generic/updates/alsa/snd-pcm-oss.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_mixer_oss (/lib/modules/2.6.32-24-generic/updates/alsa/snd-mixer-oss.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_seq_oss (/lib/modules/2.6.32-24-generic/updates/alsa/snd-seq-oss.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

dmesg showed this:

```
[ 4693.882486] snd_ac97_codec: disagrees about version of symbol snd_info_register
[ 4693.882492] snd_ac97_codec: Unknown symbol snd_info_register
[ 4693.882677] snd_ac97_codec: disagrees about version of symbol snd_ctl_add
[ 4693.882680] snd_ac97_codec: Unknown symbol snd_ctl_add
[ 4693.882860] snd_ac97_codec: disagrees about version of symbol snd_info_free_entry
[ 4693.882863] snd_ac97_codec: Unknown symbol snd_info_free_entry
[ 4693.883279] snd_ac97_codec: disagrees about version of symbol snd_ctl_find_id
[ 4693.883283] snd_ac97_codec: Unknown symbol snd_ctl_find_id
[ 4693.883383] snd_ac97_codec: disagrees about version of symbol snd_ctl_new1
[ 4693.883385] snd_ac97_codec: Unknown symbol snd_ctl_new1
[ 4693.883499] snd_ac97_codec: disagrees about version of symbol snd_ctl_remove_id
[ 4693.883501] snd_ac97_codec: Unknown symbol snd_ctl_remove_id
[ 4693.883630] snd_ac97_codec: disagrees about version of symbol snd_component_add
[ 4693.883632] snd_ac97_codec: Unknown symbol snd_component_add
[ 4693.883733] snd_ac97_codec: disagrees about version of symbol snd_ctl_make_virtual_master
[ 4693.883735] snd_ac97_codec: Unknown symbol snd_ctl_make_virtual_master
[ 4693.883830] snd_ac97_codec: disagrees about version of symbol snd_pcm_hw_rule_add
[ 4693.883832] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[ 4693.883964] snd_ac97_codec: Unknown symbol __snd_printk
[ 4693.884395] snd_ac97_codec: disagrees about version of symbol snd_ctl_boolean_mono_info
[ 4693.884398] snd_ac97_codec: Unknown symbol snd_ctl_boolean_mono_info
[ 4693.884800] snd_ac97_codec: disagrees about version of symbol _snd_ctl_add_slave
[ 4693.884802] snd_ac97_codec: Unknown symbol _snd_ctl_add_slave
[ 4693.885011] snd_ac97_codec: disagrees about version of symbol snd_info_create_card_entry
[ 4693.885013] snd_ac97_codec: Unknown symbol snd_info_create_card_entry
[ 5529.748683] snd_ac97_codec: disagrees about version of symbol snd_info_register
[ 5529.748689] snd_ac97_codec: Unknown symbol snd_info_register
[ 5529.748859] snd_ac97_codec: disagrees about version of symbol snd_ctl_add
[ 5529.748862] snd_ac97_codec: Unknown symbol snd_ctl_add
[ 5529.749037] snd_ac97_codec: disagrees about version of symbol snd_info_free_entry
[ 5529.749040] snd_ac97_codec: Unknown symbol snd_info_free_entry
[ 5529.749250] snd_ac97_codec: disagrees about version of symbol snd_ctl_find_id
[ 5529.749252] snd_ac97_codec: Unknown symbol snd_ctl_find_id
[ 5529.749353] snd_ac97_codec: disagrees about version of symbol snd_ctl_new1
[ 5529.749355] snd_ac97_codec: Unknown symbol snd_ctl_new1
[ 5529.749468] snd_ac97_codec: disagrees about version of symbol snd_ctl_remove_id
[ 5529.749471] snd_ac97_codec: Unknown symbol snd_ctl_remove_id
[ 5529.749599] snd_ac97_codec: disagrees about version of symbol snd_component_add
[ 5529.749602] snd_ac97_codec: Unknown symbol snd_component_add
[ 5529.749702] snd_ac97_codec: disagrees about version of symbol snd_ctl_make_virtual_master
[ 5529.749705] snd_ac97_codec: Unknown symbol snd_ctl_make_virtual_master
[ 5529.749799] snd_ac97_codec: disagrees about version of symbol snd_pcm_hw_rule_add
[ 5529.749801] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[ 5529.749932] snd_ac97_codec: Unknown symbol __snd_printk
[ 5529.750160] snd_ac97_codec: disagrees about version of symbol snd_ctl_boolean_mono_info
[ 5529.750162] snd_ac97_codec: Unknown symbol snd_ctl_boolean_mono_info
[ 5529.750564] snd_ac97_codec: disagrees about version of symbol _snd_ctl_add_slave
[ 5529.750566] snd_ac97_codec: Unknown symbol _snd_ctl_add_slave
[ 5529.750774] snd_ac97_codec: disagrees about version of symbol snd_info_create_card_entry
[ 5529.750777] snd_ac97_codec: Unknown symbol snd_info_create_card_entry
[ 5553.044707] snd_ac97_codec: disagrees about version of symbol snd_info_register
[ 5553.044712] snd_ac97_codec: Unknown symbol snd_info_register
[ 5553.044882] snd_ac97_codec: disagrees about version of symbol snd_ctl_add
[ 5553.044885] snd_ac97_codec: Unknown symbol snd_ctl_add
[ 5553.045073] snd_ac97_codec: disagrees about version of symbol snd_info_free_entry
[ 5553.045076] snd_ac97_codec: Unknown symbol snd_info_free_entry
[ 5553.045316] snd_ac97_codec: disagrees about version of symbol snd_ctl_find_id
[ 5553.045319] snd_ac97_codec: Unknown symbol snd_ctl_find_id
[ 5553.045418] snd_ac97_codec: disagrees about version of symbol snd_ctl_new1
[ 5553.045420] snd_ac97_codec: Unknown symbol snd_ctl_new1
[ 5553.045533] snd_ac97_codec: disagrees about version of symbol snd_ctl_remove_id
[ 5553.045535] snd_ac97_codec: Unknown symbol snd_ctl_remove_id
[ 5553.045662] snd_ac97_codec: disagrees about version of symbol snd_component_add
[ 5553.045664] snd_ac97_codec: Unknown symbol snd_component_add
[ 5553.045764] snd_ac97_codec: disagrees about version of symbol snd_ctl_make_virtual_master
[ 5553.045767] snd_ac97_codec: Unknown symbol snd_ctl_make_virtual_master
[ 5553.045860] snd_ac97_codec: disagrees about version of symbol snd_pcm_hw_rule_add
[ 5553.045863] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[ 5553.045994] snd_ac97_codec: Unknown symbol __snd_printk
[ 5553.046221] snd_ac97_codec: disagrees about version of symbol snd_ctl_boolean_mono_info
[ 5553.046223] snd_ac97_codec: Unknown symbol snd_ctl_boolean_mono_info
[ 5553.046624] snd_ac97_codec: disagrees about version of symbol _snd_ctl_add_slave
[ 5553.046626] snd_ac97_codec: Unknown symbol _snd_ctl_add_slave
[ 5553.046835] snd_ac97_codec: disagrees about version of symbol snd_info_create_card_entry
[ 5553.046837] snd_ac97_codec: Unknown symbol snd_info_create_card_entry
[ 5860.284293] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 6095.895991] snd_ac97_codec: disagrees about version of symbol snd_info_register
[ 6095.896035] snd_ac97_codec: Unknown symbol snd_info_register
[ 6095.896206] snd_ac97_codec: disagrees about version of symbol snd_ctl_add
[ 6095.896208] snd_ac97_codec: Unknown symbol snd_ctl_add
[ 6095.896384] snd_ac97_codec: disagrees about version of symbol snd_info_free_entry
[ 6095.896386] snd_ac97_codec: Unknown symbol snd_info_free_entry
[ 6095.897033] snd_ac97_codec: disagrees about version of symbol snd_ctl_find_id
[ 6095.897036] snd_ac97_codec: Unknown symbol snd_ctl_find_id
[ 6095.897137] snd_ac97_codec: disagrees about version of symbol snd_ctl_new1
[ 6095.897139] snd_ac97_codec: Unknown symbol snd_ctl_new1
[ 6095.897253] snd_ac97_codec: disagrees about version of symbol snd_ctl_remove_id
[ 6095.897255] snd_ac97_codec: Unknown symbol snd_ctl_remove_id
[ 6095.897384] snd_ac97_codec: disagrees about version of symbol snd_component_add
[ 6095.897386] snd_ac97_codec: Unknown symbol snd_component_add
[ 6095.897487] snd_ac97_codec: disagrees about version of symbol snd_ctl_make_virtual_master
[ 6095.897489] snd_ac97_codec: Unknown symbol snd_ctl_make_virtual_master
[ 6095.897583] snd_ac97_codec: disagrees about version of symbol snd_pcm_hw_rule_add
[ 6095.897586] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[ 6095.897717] snd_ac97_codec: Unknown symbol __snd_printk
[ 6095.898064] snd_ac97_codec: disagrees about version of symbol snd_ctl_boolean_mono_info
[ 6095.898067] snd_ac97_codec: Unknown symbol snd_ctl_boolean_mono_info
[ 6095.898465] snd_ac97_codec: disagrees about version of symbol _snd_ctl_add_slave
[ 6095.898468] snd_ac97_codec: Unknown symbol _snd_ctl_add_slave
[ 6095.898675] snd_ac97_codec: disagrees about version of symbol snd_info_create_card_entry
[ 6095.898677] snd_ac97_codec: Unknown symbol snd_info_create_card_entry
[ 6184.648323] snd_ac97_codec: disagrees about version of symbol snd_info_register
[ 6184.648329] snd_ac97_codec: Unknown symbol snd_info_register
[ 6184.648499] snd_ac97_codec: disagrees about version of symbol snd_ctl_add
[ 6184.648502] snd_ac97_codec: Unknown symbol snd_ctl_add
[ 6184.648677] snd_ac97_codec: disagrees about version of symbol snd_info_free_entry
[ 6184.648679] snd_ac97_codec: Unknown symbol snd_info_free_entry
[ 6184.648889] snd_ac97_codec: disagrees about version of symbol snd_ctl_find_id
[ 6184.648891] snd_ac97_codec: Unknown symbol snd_ctl_find_id
[ 6184.648991] snd_ac97_codec: disagrees about version of symbol snd_ctl_new1
[ 6184.648993] snd_ac97_codec: Unknown symbol snd_ctl_new1
[ 6184.649107] snd_ac97_codec: disagrees about version of symbol snd_ctl_remove_id
[ 6184.649109] snd_ac97_codec: Unknown symbol snd_ctl_remove_id
[ 6184.649237] snd_ac97_codec: disagrees about version of symbol snd_component_add
[ 6184.649239] snd_ac97_codec: Unknown symbol snd_component_add
[ 6184.649339] snd_ac97_codec: disagrees about version of symbol snd_ctl_make_virtual_master
[ 6184.649342] snd_ac97_codec: Unknown symbol snd_ctl_make_virtual_master
[ 6184.649435] snd_ac97_codec: disagrees about version of symbol snd_pcm_hw_rule_add
[ 6184.649438] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[ 6184.649569] snd_ac97_codec: Unknown symbol __snd_printk
[ 6184.649796] snd_ac97_codec: disagrees about version of symbol snd_ctl_boolean_mono_info
[ 6184.649798] snd_ac97_codec: Unknown symbol snd_ctl_boolean_mono_info
[ 6184.650199] snd_ac97_codec: disagrees about version of symbol _snd_ctl_add_slave
[ 6184.650201] snd_ac97_codec: Unknown symbol _snd_ctl_add_slave
[ 6184.650409] snd_ac97_codec: disagrees about version of symbol snd_info_create_card_entry
[ 6184.650411] snd_ac97_codec: Unknown symbol snd_info_create_card_entry
[ 6184.673866] snd_mixer_oss: disagrees about version of symbol snd_info_register
[ 6184.673871] snd_mixer_oss: Unknown symbol snd_info_register
[ 6184.673971] snd_mixer_oss: disagrees about version of symbol snd_info_free_entry
[ 6184.673974] snd_mixer_oss: Unknown symbol snd_info_free_entry
[ 6184.676508] snd_mixer_oss: disagrees about version of symbol snd_unregister_oss_device
[ 6184.676514] snd_mixer_oss: Unknown symbol snd_unregister_oss_device
[ 6184.676616] snd_mixer_oss: disagrees about version of symbol snd_ctl_find_id
[ 6184.676619] snd_mixer_oss: Unknown symbol snd_ctl_find_id
[ 6184.676719] snd_mixer_oss: disagrees about version of symbol snd_register_oss_device
[ 6184.676721] snd_mixer_oss: Unknown symbol snd_register_oss_device
[ 6184.676824] snd_mixer_oss: disagrees about version of symbol snd_card_file_add
[ 6184.676826] snd_mixer_oss: Unknown symbol snd_card_file_add
[ 6184.676926] snd_mixer_oss: disagrees about version of symbol snd_mixer_oss_notify_callback
[ 6184.676928] snd_mixer_oss: Unknown symbol snd_mixer_oss_notify_callback
[ 6184.677072] snd_mixer_oss: Unknown symbol __snd_printk
[ 6184.677268] snd_mixer_oss: disagrees about version of symbol snd_cards
[ 6184.677270] snd_mixer_oss: Unknown symbol snd_cards
[ 6184.677438] snd_mixer_oss: disagrees about version of symbol snd_ctl_notify
[ 6184.677440] snd_mixer_oss: Unknown symbol snd_ctl_notify
[ 6184.677873] snd_mixer_oss: disagrees about version of symbol snd_info_create_card_entry
[ 6184.677875] snd_mixer_oss: Unknown symbol snd_info_create_card_entry
[ 6184.677983] snd_mixer_oss: disagrees about version of symbol snd_card_file_remove
[ 6184.677986] snd_mixer_oss: Unknown symbol snd_card_file_remove
[ 6184.678084] snd_mixer_oss: disagrees about version of symbol snd_ctl_find_numid
[ 6184.678087] snd_mixer_oss: Unknown symbol snd_ctl_find_numid
[ 6184.698669] snd_mixer_oss: disagrees about version of symbol snd_info_register
[ 6184.698675] snd_mixer_oss: Unknown symbol snd_info_register
[ 6184.698776] snd_mixer_oss: disagrees about version of symbol snd_info_free_entry
[ 6184.698779] snd_mixer_oss: Unknown symbol snd_info_free_entry
[ 6184.698990] snd_mixer_oss: disagrees about version of symbol snd_unregister_oss_device
[ 6184.698993] snd_mixer_oss: Unknown symbol snd_unregister_oss_device
[ 6184.699095] snd_mixer_oss: disagrees about version of symbol snd_ctl_find_id
[ 6184.699097] snd_mixer_oss: Unknown symbol snd_ctl_find_id
[ 6184.699196] snd_mixer_oss: disagrees about version of symbol snd_register_oss_device
[ 6184.699199] snd_mixer_oss: Unknown symbol snd_register_oss_device
[ 6184.699318] snd_mixer_oss: disagrees about version of symbol snd_card_file_add
[ 6184.699320] snd_mixer_oss: Unknown symbol snd_card_file_add
[ 6184.699420] snd_mixer_oss: disagrees about version of symbol snd_mixer_oss_notify_callback
[ 6184.699422] snd_mixer_oss: Unknown symbol snd_mixer_oss_notify_callback
[ 6184.699558] snd_mixer_oss: Unknown symbol __snd_printk
[ 6184.699754] snd_mixer_oss: disagrees about version of symbol snd_cards
[ 6184.699756] snd_mixer_oss: Unknown symbol snd_cards
[ 6184.699917] snd_mixer_oss: disagrees about version of symbol snd_ctl_notify
[ 6184.699919] snd_mixer_oss: Unknown symbol snd_ctl_notify
[ 6184.700386] snd_mixer_oss: disagrees about version of symbol snd_info_create_card_entry
[ 6184.700389] snd_mixer_oss: Unknown symbol snd_info_create_card_entry
[ 6184.700496] snd_mixer_oss: disagrees about version of symbol snd_card_file_remove
[ 6184.700499] snd_mixer_oss: Unknown symbol snd_card_file_remove
[ 6184.700597] snd_mixer_oss: disagrees about version of symbol snd_ctl_find_numid
[ 6184.700599] snd_mixer_oss: Unknown symbol snd_ctl_find_numid
[ 6184.724399] snd_seq_oss: disagrees about version of symbol snd_info_register
[ 6184.724404] snd_seq_oss: Unknown symbol snd_info_register
[ 6184.724627] snd_seq_oss: disagrees about version of symbol snd_info_create_module_entry
[ 6184.724629] snd_seq_oss: Unknown symbol snd_info_create_module_entry
[ 6184.725028] snd_seq_oss: disagrees about version of symbol snd_info_free_entry
[ 6184.725030] snd_seq_oss: Unknown symbol snd_info_free_entry
[ 6184.725130] snd_seq_oss: disagrees about version of symbol snd_seq_root
[ 6184.725132] snd_seq_oss: Unknown symbol snd_seq_root
[ 6184.725337] snd_seq_oss: disagrees about version of symbol snd_unregister_oss_device
[ 6184.725339] snd_seq_oss: Unknown symbol snd_unregister_oss_device
[ 6184.725540] snd_seq_oss: disagrees about version of symbol snd_register_oss_device
[ 6184.725542] snd_seq_oss: Unknown symbol snd_register_oss_device
[ 6184.725645] snd_seq_oss: disagrees about version of symbol snd_seq_device_register_driver
[ 6184.725647] snd_seq_oss: Unknown symbol snd_seq_device_register_driver
[ 6184.725881] snd_seq_oss: Unknown symbol __snd_printk
[ 6184.726864] snd_seq_oss: disagrees about version of symbol snd_seq_create_kernel_client
[ 6184.726866] snd_seq_oss: Unknown symbol snd_seq_create_kernel_client
[ 6239.634946] REISERFS (device sda7): found reiserfs format "3.6" with standard journal
[ 6239.634968] REISERFS (device sda7): using ordered data mode
[ 6239.646149] REISERFS (device sda7): journal params: device sda7, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[ 6239.646646] REISERFS (device sda7): checking transaction log (sda7)
[ 6239.655917] REISERFS (device sda7): Using r5 hash to sort names
[ 7890.160131] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[ 7890.176526] SGI XFS Quota Management subsystem
[ 7890.215066] JFS: nTxBlock = 8192, nTxLock = 65536
[ 7890.285772] NTFS driver 2.1.29 [Flags: R/O MODULE].
[ 7890.349370] QNX4 filesystem 0.2.3 registered.
[ 7890.488164] Btrfs loaded
[ 7892.559168] REISERFS (device sda6): found reiserfs format "3.6" with standard journal
[ 7892.559248] REISERFS (device sda6): using ordered data mode
[ 7892.571619] REISERFS (device sda6): journal params: device sda6, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[ 7892.572093] REISERFS (device sda6): checking transaction log (sda6)
[ 7892.597759] REISERFS (device sda6): Using r5 hash to sort names
[ 7894.075883] REISERFS (device sda6): found reiserfs format "3.6" with standard journal
[ 7894.075952] REISERFS (device sda6): using ordered data mode
[ 7894.076797] REISERFS (device sda6): journal params: device sda6, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[ 7894.077198] REISERFS (device sda6): checking transaction log (sda6)
[ 7894.105327] REISERFS (device sda6): Using r5 hash to sort names
[ 8063.203945] snd_ac97_codec: disagrees about version of symbol snd_info_register
[ 8063.203950] snd_ac97_codec: Unknown symbol snd_info_register
[ 8063.204153] snd_ac97_codec: disagrees about version of symbol snd_ctl_add
[ 8063.204156] snd_ac97_codec: Unknown symbol snd_ctl_add
[ 8063.204366] snd_ac97_codec: disagrees about version of symbol snd_info_free_entry
[ 8063.204368] snd_ac97_codec: Unknown symbol snd_info_free_entry
[ 8063.205758] snd_ac97_codec: disagrees about version of symbol snd_ctl_find_id
[ 8063.205763] snd_ac97_codec: Unknown symbol snd_ctl_find_id
[ 8063.205865] snd_ac97_codec: disagrees about version of symbol snd_ctl_new1
[ 8063.205868] snd_ac97_codec: Unknown symbol snd_ctl_new1
[ 8063.205982] snd_ac97_codec: disagrees about version of symbol snd_ctl_remove_id
[ 8063.205984] snd_ac97_codec: Unknown symbol snd_ctl_remove_id
[ 8063.206114] snd_ac97_codec: disagrees about version of symbol snd_component_add
[ 8063.206116] snd_ac97_codec: Unknown symbol snd_component_add
[ 8063.206218] snd_ac97_codec: disagrees about version of symbol snd_ctl_make_virtual_master
[ 8063.206220] snd_ac97_codec: Unknown symbol snd_ctl_make_virtual_master
[ 8063.206316] snd_ac97_codec: disagrees about version of symbol snd_pcm_hw_rule_add
[ 8063.206318] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[ 8063.206452] snd_ac97_codec: Unknown symbol __snd_printk
[ 8063.206684] snd_ac97_codec: disagrees about version of symbol snd_ctl_boolean_mono_info
[ 8063.206687] snd_ac97_codec: Unknown symbol snd_ctl_boolean_mono_info
[ 8063.207101] snd_ac97_codec: disagrees about version of symbol _snd_ctl_add_slave
[ 8063.207103] snd_ac97_codec: Unknown symbol _snd_ctl_add_slave
[ 8063.207313] snd_ac97_codec: disagrees about version of symbol snd_info_create_card_entry
[ 8063.207316] snd_ac97_codec: Unknown symbol snd_info_create_card_entry
[ 8063.235773] snd_mixer_oss: disagrees about version of symbol snd_info_register
[ 8063.235778] snd_mixer_oss: Unknown symbol snd_info_register
[ 8063.235881] snd_mixer_oss: disagrees about version of symbol snd_info_free_entry
[ 8063.235883] snd_mixer_oss: Unknown symbol snd_info_free_entry
[ 8063.236485] snd_mixer_oss: disagrees about version of symbol snd_unregister_oss_device
[ 8063.236489] snd_mixer_oss: Unknown symbol snd_unregister_oss_device
[ 8063.236595] snd_mixer_oss: disagrees about version of symbol snd_ctl_find_id
[ 8063.236597] snd_mixer_oss: Unknown symbol snd_ctl_find_id
[ 8063.236699] snd_mixer_oss: disagrees about version of symbol snd_register_oss_device
[ 8063.236702] snd_mixer_oss: Unknown symbol snd_register_oss_device
[ 8063.236805] snd_mixer_oss: disagrees about version of symbol snd_card_file_add
[ 8063.236808] snd_mixer_oss: Unknown symbol snd_card_file_add
[ 8063.236909] snd_mixer_oss: disagrees about version of symbol snd_mixer_oss_notify_callback
[ 8063.236912] snd_mixer_oss: Unknown symbol snd_mixer_oss_notify_callback
[ 8063.237057] snd_mixer_oss: Unknown symbol __snd_printk
[ 8063.237258] snd_mixer_oss: disagrees about version of symbol snd_cards
[ 8063.237260] snd_mixer_oss: Unknown symbol snd_cards
[ 8063.237424] snd_mixer_oss: disagrees about version of symbol snd_ctl_notify
[ 8063.237426] snd_mixer_oss: Unknown symbol snd_ctl_notify
[ 8063.237877] snd_mixer_oss: disagrees about version of symbol snd_info_create_card_entry
[ 8063.237879] snd_mixer_oss: Unknown symbol snd_info_create_card_entry
[ 8063.237991] snd_mixer_oss: disagrees about version of symbol snd_card_file_remove
[ 8063.237993] snd_mixer_oss: Unknown symbol snd_card_file_remove
[ 8063.238094] snd_mixer_oss: disagrees about version of symbol snd_ctl_find_numid
[ 8063.238096] snd_mixer_oss: Unknown symbol snd_ctl_find_numid
[ 8063.255900] snd_mixer_oss: disagrees about version of symbol snd_info_register
[ 8063.255906] snd_mixer_oss: Unknown symbol snd_info_register
[ 8063.256049] snd_mixer_oss: disagrees about version of symbol snd_info_free_entry
[ 8063.256052] snd_mixer_oss: Unknown symbol snd_info_free_entry
[ 8063.258709] snd_mixer_oss: disagrees about version of symbol snd_unregister_oss_device
[ 8063.258714] snd_mixer_oss: Unknown symbol snd_unregister_oss_device
[ 8063.258818] snd_mixer_oss: disagrees about version of symbol snd_ctl_find_id
[ 8063.258820] snd_mixer_oss: Unknown symbol snd_ctl_find_id
[ 8063.258922] snd_mixer_oss: disagrees about version of symbol snd_register_oss_device
[ 8063.258925] snd_mixer_oss: Unknown symbol snd_register_oss_device
[ 8063.259028] snd_mixer_oss: disagrees about version of symbol snd_card_file_add
[ 8063.259030] snd_mixer_oss: Unknown symbol snd_card_file_add
[ 8063.259132] snd_mixer_oss: disagrees about version of symbol snd_mixer_oss_notify_callback
[ 8063.259134] snd_mixer_oss: Unknown symbol snd_mixer_oss_notify_callback
[ 8063.259274] snd_mixer_oss: Unknown symbol __snd_printk
[ 8063.259474] snd_mixer_oss: disagrees about version of symbol snd_cards
[ 8063.259476] snd_mixer_oss: Unknown symbol snd_cards
[ 8063.259639] snd_mixer_oss: disagrees about version of symbol snd_ctl_notify
[ 8063.259641] snd_mixer_oss: Unknown symbol snd_ctl_notify
[ 8063.260144] snd_mixer_oss: disagrees about version of symbol snd_info_create_card_entry
[ 8063.260147] snd_mixer_oss: Unknown symbol snd_info_create_card_entry
[ 8063.260259] snd_mixer_oss: disagrees about version of symbol snd_card_file_remove
[ 8063.260261] snd_mixer_oss: Unknown symbol snd_card_file_remove
[ 8063.260362] snd_mixer_oss: disagrees about version of symbol snd_ctl_find_numid
[ 8063.260364] snd_mixer_oss: Unknown symbol snd_ctl_find_numid
[ 8063.294683] snd_seq_oss: disagrees about version of symbol snd_info_register
[ 8063.294688] snd_seq_oss: Unknown symbol snd_info_register
[ 8063.294912] snd_seq_oss: disagrees about version of symbol snd_info_create_module_entry
[ 8063.294914] snd_seq_oss: Unknown symbol snd_info_create_module_entry
[ 8063.295332] snd_seq_oss: disagrees about version of symbol snd_info_free_entry
[ 8063.295335] snd_seq_oss: Unknown symbol snd_info_free_entry
[ 8063.295436] snd_seq_oss: disagrees about version of symbol snd_seq_root
[ 8063.295439] snd_seq_oss: Unknown symbol snd_seq_root
[ 8063.295648] snd_seq_oss: disagrees about version of symbol snd_unregister_oss_device
[ 8063.295650] snd_seq_oss: Unknown symbol snd_unregister_oss_device
[ 8063.295855] snd_seq_oss: disagrees about version of symbol snd_register_oss_device
[ 8063.295857] snd_seq_oss: Unknown symbol snd_register_oss_device
[ 8063.295962] snd_seq_oss: disagrees about version of symbol snd_seq_device_register_driver
[ 8063.295964] snd_seq_oss: Unknown symbol snd_seq_device_register_driver
[ 8063.297039] snd_seq_oss: Unknown symbol __snd_printk
[ 8063.298034] snd_seq_oss: disagrees about version of symbol snd_seq_create_kernel_client
[ 8063.298036] snd_seq_oss: Unknown symbol snd_seq_create_kernel_client

```

What to do? I think the answer may vary depending on the exact crash log.
Please help, trying to install this driver has left me in despair( 
](*,):evil:
Thanks in advance :P
PS
Maybe it's easier to install Ubuntu Studio?

---

