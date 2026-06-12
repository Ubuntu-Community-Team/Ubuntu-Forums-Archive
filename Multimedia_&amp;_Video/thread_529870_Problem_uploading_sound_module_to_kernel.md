---
title: "Problem uploading sound module to kernel"
date: 2007-08-19
forum: Multimedia &amp; Video
---

### Post by johnapeterson on 2007-08-19
Hello,
I am having a problem with uploading my ice1712 sound module onto the kernel.  I have followed the directions on this site:

[http://www.alsa-project.org/main/index.php/Matrix:Module-ice1712](http://www.alsa-project.org/main/index.php/Matrix:Module-ice1712)

But when "modprobe snd-ice1712"

I get the following:

john@john-desktop:/usr/src/alsa/alsa-driver-1.0.14$ sudo modprobe snd-ice1712
FATAL: Error inserting snd (/lib/modules/2.6.20-16-lowlatency/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.20-16-lowlatency/kernel/sound/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.20-16-lowlatency/kernel/sound/acore/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_mpu401_uart (/lib/modules/2.6.20-16-lowlatency/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_i2c (/lib/modules/2.6.20-16-lowlatency/kernel/sound/i2c/snd-i2c.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.20-16-lowlatency/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.20-16-lowlatency/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.20-16-lowlatency/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.20-16-lowlatency/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.20-16-lowlatency/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_cs8427 (/lib/modules/2.6.20-16-lowlatency/kernel/sound/i2c/snd-cs8427.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ak4xxx_adda (/lib/modules/2.6.20-16-lowlatency/kernel/sound/i2c/other/snd-ak4xxx-adda.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ice17xx_ak4xxx (/lib/modules/2.6.20-16-lowlatency/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ice1712 (/lib/modules/2.6.20-16-lowlatency/kernel/sound/pci/ice1712/snd-ice1712.ko): Unknown symbol in module, or unknown parameter (see dmesg)


And typing on "dmesg" I get:

[24988.652469] snd_mpu401_uart: Unknown symbol snd_rawmidi_transmit_ack
[24988.652645] snd_mpu401_uart: Unknown symbol release_and_free_resource
[24988.652832] snd_mpu401_uart: Unknown symbol snd_rawmidi_transmit_peek
[24988.653016] snd_mpu401_uart: Unknown symbol snd_rawmidi_new
[24988.653185] snd_mpu401_uart: Unknown symbol snd_rawmidi_set_ops
[24988.653362] snd_mpu401_uart: Unknown symbol snd_device_free
[24988.654517] snd_i2c: Unknown symbol snd_device_new
[24988.661962] snd_i2c: Unknown symbol snd_device_free
[24988.663628] snd_timer: Unknown symbol snd_info_register
[24988.663834] snd_timer: Unknown symbol snd_info_create_module_entry
[24988.664020] snd_timer: Unknown symbol snd_info_free_entry
[24988.664199] snd_timer: Unknown symbol snd_verbose_printk
[24988.664364] snd_timer: Unknown symbol snd_iprintf
[24988.664531] snd_timer: Unknown symbol snd_ecards_limit
[24988.664705] snd_timer: Unknown symbol snd_oss_info_register
[24988.664864] snd_timer: Unknown symbol snd_unregister_device
[24988.665047] snd_timer: Unknown symbol snd_device_new
[24988.665239] snd_timer: Unknown symbol snd_register_device_for_dev
[24988.703956] snd: Unknown symbol unregister_sound_special
[24988.704473] snd: Unknown symbol register_sound_special_device
[24988.705438] snd: Unknown symbol sound_class
[24988.707453] snd_timer: Unknown symbol snd_info_register
[24988.707904] snd_timer: Unknown symbol snd_info_create_module_entry
[24988.708178] snd_timer: Unknown symbol snd_info_free_entry
[24988.708450] snd_timer: Unknown symbol snd_verbose_printk
[24988.708734] snd_timer: Unknown symbol snd_iprintf
[24988.708997] snd_timer: Unknown symbol snd_ecards_limit
[24988.709288] snd_timer: Unknown symbol snd_oss_info_register
[24988.709540] snd_timer: Unknown symbol snd_unregister_device
[24988.709972] snd_timer: Unknown symbol snd_device_new
[24988.710260] snd_timer: Unknown symbol snd_register_device_for_dev
[24988.721108] snd_pcm: Unknown symbol snd_info_register
[24988.721546] snd_pcm: Unknown symbol snd_info_create_module_entry
[24988.721860] snd_pcm: Unknown symbol snd_timer_notify
[24988.722164] snd_pcm: Unknown symbol snd_timer_interrupt
[24988.722418] snd_pcm: Unknown symbol snd_info_free_entry
[24988.722670] snd_pcm: Unknown symbol snd_add_device_sysfs_file
[24988.722946] snd_pcm: Unknown symbol snd_info_get_str
[24988.723229] snd_pcm: Unknown symbol snd_verbose_printk
[24988.723519] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[24988.723769] snd_pcm: Unknown symbol snd_card_file_add
[24988.724027] snd_pcm: Unknown symbol snd_iprintf
[24988.724289] snd_pcm: Unknown symbol snd_major
[24988.724572] snd_pcm: Unknown symbol snd_unregister_device
[24988.724843] snd_pcm: Unknown symbol snd_timer_new
[24988.725074] snd_pcm: Unknown symbol snd_device_new
[24988.725334] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[24988.725628] snd_pcm: Unknown symbol snd_lookup_minor_data
[24988.725896] snd_pcm: Unknown symbol snd_info_create_card_entry
[24988.726156] snd_pcm: Unknown symbol snd_power_wait
[24988.726399] snd_pcm: Unknown symbol snd_device_free
[24988.726659] snd_pcm: Unknown symbol snd_card_file_remove
[24988.726910] snd_pcm: Unknown symbol snd_register_device_for_dev
[24988.727220] snd_pcm: Unknown symbol snd_device_register
[24988.727464] snd_pcm: Unknown symbol snd_info_get_line
[24988.730809] snd_ac97_codec: Unknown symbol snd_info_register
[24988.731008] snd_ac97_codec: Unknown symbol snd_ctl_add
[24988.731194] snd_ac97_codec: Unknown symbol snd_info_free_entry
[24988.731375] snd_ac97_codec: Unknown symbol snd_interval_refine
[24988.731552] snd_ac97_codec: Unknown symbol snd_ctl_find_id
[24988.731708] snd_ac97_codec: Unknown symbol snd_verbose_printk
[24988.731873] snd_ac97_codec: Unknown symbol snd_ctl_new1
[24988.732028] snd_ac97_codec: Unknown symbol snd_ctl_remove_id
[24988.732198] snd_ac97_codec: Unknown symbol snd_component_add
[24988.732358] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[24988.732537] snd_ac97_codec: Unknown symbol snd_iprintf
[24988.732747] snd_ac97_codec: Unknown symbol snd_device_new
[24988.732939] snd_ac97_codec: Unknown symbol snd_info_create_card_entry
[24988.734470] snd_cs8427: Unknown symbol snd_ctl_add
[24988.734674] snd_cs8427: Unknown symbol snd_verbose_printk
[24988.734837] snd_cs8427: Unknown symbol snd_ctl_new1
[24988.734982] snd_cs8427: Unknown symbol snd_i2c_readbytes
[24988.735138] snd_cs8427: Unknown symbol snd_i2c_device_free
[24988.735295] snd_cs8427: Unknown symbol snd_ctl_notify
[24988.735448] snd_cs8427: Unknown symbol snd_i2c_sendbytes
[24988.735609] snd_cs8427: Unknown symbol snd_i2c_device_create
[24988.736812] snd_ak4xxx_adda: Unknown symbol snd_ctl_add
[24988.736991] snd_ak4xxx_adda: Unknown symbol snd_ctl_new1
[24988.738202] snd_ice17xx_ak4xxx: Unknown symbol snd_akm4xxx_init
[24988.738417] snd_ice17xx_ak4xxx: Unknown symbol snd_akm4xxx_build_controls
[24988.741342] snd_ice1712: Unknown symbol snd_ice1712_akm4xxx_init
[24988.741587] snd_ice1712: Unknown symbol snd_ctl_add
[24988.741739] snd_ice1712: Unknown symbol snd_pcm_new
[24988.741907] snd_ice1712: Unknown symbol snd_card_register
[24988.742061] snd_ice1712: Unknown symbol snd_card_free
[24988.742209] snd_ice1712: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[24988.742398] snd_ice1712: Unknown symbol snd_card_proc_new
[24988.749695] snd_ice1712: Unknown symbol snd_akm4xxx_write
[24988.749883] snd_ice1712: Unknown symbol snd_cs8427_iec958_active
[24988.750087] snd_ice1712: Unknown symbol snd_ac97_set_rate
[24988.750260] snd_ice1712: Unknown symbol snd_ac97_mixer
[24988.750414] snd_ice1712: Unknown symbol snd_ac97_bus
[24988.750564] snd_ice1712: Unknown symbol snd_pcm_set_sync
[24988.750729] snd_ice1712: Unknown symbol snd_verbose_printk
[24988.750890] snd_ice1712: Unknown symbol snd_cs8427_iec958_pcm
[24988.751051] snd_ice1712: Unknown symbol snd_ctl_new1
[24988.751202] snd_ice1712: Unknown symbol snd_i2c_readbytes
[24988.751368] snd_ice1712: Unknown symbol snd_i2c_bus_create
[24988.751532] snd_ice1712: Unknown symbol snd_ice1712_akm4xxx_free
[24988.751700] snd_ice1712: Unknown symbol snd_cs8427_create
[24988.751858] snd_ice1712: Unknown symbol snd_card_new
[24988.752005] snd_ice1712: Unknown symbol snd_iprintf
[24988.752153] snd_ice1712: Unknown symbol snd_pcm_lib_malloc_pages
[24988.752325] snd_ice1712: Unknown symbol snd_pcm_lib_ioctl
[24988.752488] snd_ice1712: Unknown symbol snd_pcm_lib_free_pages
[24988.752652] snd_ice1712: Unknown symbol snd_cs8427_iec958_build
[24988.752821] snd_ice1712: Unknown symbol snd_akm4xxx_reset
[24988.752983] snd_ice1712: Unknown symbol snd_ctl_notify
[24988.753132] snd_ice1712: Unknown symbol snd_pcm_set_ops
[24988.753296] snd_ice1712: Unknown symbol snd_pcm_hw_constraint_list
[24988.753480] snd_ice1712: Unknown symbol snd_device_new
[24988.753629] snd_ice1712: Unknown symbol snd_cs8427_reg_write
[24988.753792] snd_ice1712: Unknown symbol snd_mpu401_uart_interrupt
[24988.754021] snd_ice1712: Unknown symbol snd_i2c_sendbytes
[24988.754179] snd_ice1712: Unknown symbol snd_ice1712_akm4xxx_build_controls
[24988.754366] snd_ice1712: Unknown symbol snd_mpu401_uart_new
[24988.754538] snd_ice1712: Unknown symbol snd_pcm_hw_constraint_msbits
[24988.754717] snd_ice1712: Unknown symbol snd_i2c_device_create
[24988.754874] snd_ice1712: Unknown symbol snd_pcm_period_elapsed
[24988.755027] snd_ice1712: Unknown symbol snd_pcm_format_width
[25101.708772] snd: Unknown symbol unregister_sound_special
[25101.709345] snd: Unknown symbol register_sound_special_device
[25101.709896] snd: Unknown symbol sound_class
[25101.822965] snd: Unknown symbol unregister_sound_special
[25101.823503] snd: Unknown symbol register_sound_special_device
[25101.824066] snd: Unknown symbol sound_class
[25101.947481] snd: Unknown symbol unregister_sound_special
[25101.948029] snd: Unknown symbol register_sound_special_device
[25101.948584] snd: Unknown symbol sound_class
[25102.048329] snd: Unknown symbol unregister_sound_special
[25102.049140] snd: Unknown symbol register_sound_special_device
[25102.049715] snd: Unknown symbol sound_class
[25102.147490] snd: Unknown symbol unregister_sound_special
[25102.148017] snd: Unknown symbol register_sound_special_device
[25102.148587] snd: Unknown symbol sound_class
[25102.222688] snd: Unknown symbol unregister_sound_special
[25102.223248] snd: Unknown symbol register_sound_special_device
[25102.223808] snd: Unknown symbol sound_class
[25102.298415] snd: Unknown symbol unregister_sound_special
[25102.298941] snd: Unknown symbol register_sound_special_device
[25102.299497] snd: Unknown symbol sound_class
[25102.399330] snd: Unknown symbol unregister_sound_special
[25102.399928] snd: Unknown symbol register_sound_special_device
[25102.400487] snd: Unknown symbol sound_class
[25113.576913] snd: Unknown symbol unregister_sound_special
[25113.577054] snd: Unknown symbol register_sound_special_device
[25113.577402] snd: Unknown symbol sound_class
[25113.658681] snd: Unknown symbol unregister_sound_special
[25113.658960] snd: Unknown symbol register_sound_special_device
[25113.659408] snd: Unknown symbol sound_class
[25113.732829] snd: Unknown symbol unregister_sound_special
[25113.732974] snd: Unknown symbol register_sound_special_device
[25113.733333] snd: Unknown symbol sound_class
[25113.807645] snd: Unknown symbol unregister_sound_special
[25113.807790] snd: Unknown symbol register_sound_special_device
[25113.808149] snd: Unknown symbol sound_class
[25113.884116] snd: Unknown symbol unregister_sound_special
[25113.884394] snd: Unknown symbol register_sound_special_device
[25113.884840] snd: Unknown symbol sound_class
[25113.960232] snd: Unknown symbol unregister_sound_special
[25113.960524] snd: Unknown symbol register_sound_special_device
[25113.960973] snd: Unknown symbol sound_class
[25114.043668] snd: Unknown symbol unregister_sound_special
[25114.044184] snd: Unknown symbol register_sound_special_device
[25114.044749] snd: Unknown symbol sound_class
[25114.118262] snd: Unknown symbol unregister_sound_special
[25114.118802] snd: Unknown symbol register_sound_special_device
[25114.119360] snd: Unknown symbol sound_class
[25184.721324] snd: Unknown symbol unregister_sound_special
[25184.721858] snd: Unknown symbol register_sound_special_device
[25184.722412] snd: Unknown symbol sound_class
[25184.724339] snd_mixer_oss: Unknown symbol snd_info_register
[25184.724534] snd_mixer_oss: Unknown symbol snd_info_free_entry
[25184.724711] snd_mixer_oss: Unknown symbol snd_info_get_str
[25184.724874] snd_mixer_oss: Unknown symbol snd_unregister_oss_device
[25184.725051] snd_mixer_oss: Unknown symbol snd_ctl_find_id
[25184.725216] snd_mixer_oss: Unknown symbol snd_verbose_printk
[25184.725375] snd_mixer_oss: Unknown symbol snd_register_oss_device
[25184.725544] snd_mixer_oss: Unknown symbol snd_card_file_add
[25184.725703] snd_mixer_oss: Unknown symbol snd_mixer_oss_notify_callback
[25184.725894] snd_mixer_oss: Unknown symbol snd_iprintf
[25184.726044] snd_mixer_oss: Unknown symbol snd_cards
[25184.726214] snd_mixer_oss: Unknown symbol snd_ctl_notify
[25184.726368] snd_mixer_oss: Unknown symbol snd_oss_info_register
[25184.726569] snd_mixer_oss: Unknown symbol snd_lookup_oss_minor_data
[25184.726755] snd_mixer_oss: Unknown symbol snd_info_create_card_entry
[25184.726940] snd_mixer_oss: Unknown symbol snd_card_file_remove
[25184.727232] snd_mixer_oss: Unknown symbol snd_ctl_find_numid
[25184.727399] snd_mixer_oss: Unknown symbol snd_info_get_line
[25184.728921] snd_timer: Unknown symbol snd_info_register
[25184.729131] snd_timer: Unknown symbol snd_info_create_module_entry
[25184.729309] snd_timer: Unknown symbol snd_info_free_entry
[25184.729487] snd_timer: Unknown symbol snd_verbose_printk
[25184.729652] snd_timer: Unknown symbol snd_iprintf
[25184.729819] snd_timer: Unknown symbol snd_ecards_limit
[25184.729987] snd_timer: Unknown symbol snd_oss_info_register
[25184.730153] snd_timer: Unknown symbol snd_unregister_device
[25184.730330] snd_timer: Unknown symbol snd_device_new
[25184.730521] snd_timer: Unknown symbol snd_register_device_for_dev
[25184.766977] snd: Unknown symbol unregister_sound_special
[25184.767505] snd: Unknown symbol register_sound_special_device
[25184.768064] snd: Unknown symbol sound_class
[25184.770152] snd_timer: Unknown symbol snd_info_register
[25184.770576] snd_timer: Unknown symbol snd_info_create_module_entry
[25184.770863] snd_timer: Unknown symbol snd_info_free_entry
[25184.771146] snd_timer: Unknown symbol snd_verbose_printk
[25184.771405] snd_timer: Unknown symbol snd_iprintf
[25184.771663] snd_timer: Unknown symbol snd_ecards_limit
[25184.771925] snd_timer: Unknown symbol snd_oss_info_register
[25184.772194] snd_timer: Unknown symbol snd_unregister_device
[25184.772460] snd_timer: Unknown symbol snd_device_new
[25184.772743] snd_timer: Unknown symbol snd_register_device_for_dev
[25184.776154] snd_pcm: Unknown symbol snd_info_register
[25184.776572] snd_pcm: Unknown symbol snd_info_create_module_entry
[25184.776875] snd_pcm: Unknown symbol snd_timer_notify
[25184.777137] snd_pcm: Unknown symbol snd_timer_interrupt
[25184.777379] snd_pcm: Unknown symbol snd_info_free_entry
[25184.777619] snd_pcm: Unknown symbol snd_add_device_sysfs_file
[25184.777889] snd_pcm: Unknown symbol snd_info_get_str
[25184.782928] snd_pcm: Unknown symbol snd_verbose_printk
[25184.783251] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[25184.783497] snd_pcm: Unknown symbol snd_card_file_add
[25184.783752] snd_pcm: Unknown symbol snd_iprintf
[25184.784022] snd_pcm: Unknown symbol snd_major
[25184.784309] snd_pcm: Unknown symbol snd_unregister_device
[25184.784573] snd_pcm: Unknown symbol snd_timer_new
[25184.784809] snd_pcm: Unknown symbol snd_device_new
[25184.785113] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[25184.785414] snd_pcm: Unknown symbol snd_lookup_minor_data
[25184.785676] snd_pcm: Unknown symbol snd_info_create_card_entry
[25184.785944] snd_pcm: Unknown symbol snd_power_wait
[25184.786189] snd_pcm: Unknown symbol snd_device_free
[25184.786445] snd_pcm: Unknown symbol snd_card_file_remove
[25184.786685] snd_pcm: Unknown symbol snd_register_device_for_dev
[25184.787028] snd_pcm: Unknown symbol snd_device_register
[25184.787279] snd_pcm: Unknown symbol snd_info_get_line
[25184.791219] snd_pcm_oss: Unknown symbol snd_pcm_lib_read
[25184.791413] snd_pcm_oss: Unknown symbol snd_pcm_hw_param_first
[25184.791577] snd_pcm_oss: Unknown symbol snd_info_register
[25184.791751] snd_pcm_oss: Unknown symbol snd_pcm_kernel_ioctl
[25184.791915] snd_pcm_oss: Unknown symbol snd_info_free_entry
[25184.792078] snd_pcm_oss: Unknown symbol snd_pcm_format_unsigned
[25184.792251] snd_pcm_oss: Unknown symbol _snd_pcm_hw_params_any
[25184.792418] snd_pcm_oss: Unknown symbol snd_info_get_str
[25184.792570] snd_pcm_oss: Unknown symbol snd_interval_refine
[25184.792736] snd_pcm_oss: Unknown symbol snd_pcm_format_physical_width
[25184.792911] snd_pcm_oss: Unknown symbol snd_unregister_oss_device
[25184.799747] snd_pcm_oss: Unknown symbol snd_pcm_format_silence_64
[25184.799962] snd_pcm_oss: Unknown symbol snd_verbose_printk
[25184.800118] snd_pcm_oss: Unknown symbol snd_pcm_open_substream
[25184.800281] snd_pcm_oss: Unknown symbol snd_register_oss_device
[25184.800446] snd_pcm_oss: Unknown symbol snd_pcm_lib_readv
[25184.800611] snd_pcm_oss: Unknown symbol snd_card_file_add
[25184.800773] snd_pcm_oss: Unknown symbol snd_pcm_lib_writev
[25184.800941] snd_pcm_oss: Unknown symbol snd_mixer_oss_ioctl_card
[25184.801108] snd_pcm_oss: Unknown symbol snd_iprintf
[25184.801261] snd_pcm_oss: Unknown symbol snd_pcm_format_linear
[25184.801423] snd_pcm_oss: Unknown symbol snd_pcm_mmap_data
[25184.801595] snd_pcm_oss: Unknown symbol snd_oss_info_register
[25184.801760] snd_pcm_oss: Unknown symbol snd_pcm_hw_param_last
[25184.802027] snd_pcm_oss: Unknown symbol snd_pcm_hw_param_value
[25184.802193] snd_pcm_oss: Unknown symbol snd_pcm_build_linear_format
[25184.802371] snd_pcm_oss: Unknown symbol snd_pcm_format_signed
[25184.802533] snd_pcm_oss: Unknown symbol snd_pcm_link_rwlock
[25184.802716] snd_pcm_oss: Unknown symbol snd_lookup_oss_minor_data
[25184.802895] snd_pcm_oss: Unknown symbol snd_pcm_hw_refine
[25184.803073] snd_pcm_oss: Unknown symbol snd_info_create_card_entry
[25184.803244] snd_pcm_oss: Unknown symbol snd_pcm_format_big_endian
[25184.803420] snd_pcm_oss: Unknown symbol snd_pcm_notify
[25184.803570] snd_pcm_oss: Unknown symbol snd_pcm_release_substream
[25184.803741] snd_pcm_oss: Unknown symbol snd_pcm_lib_write
[25184.803898] snd_pcm_oss: Unknown symbol snd_card_file_remove
[25184.804058] snd_pcm_oss: Unknown symbol snd_pcm_format_set_silence
[25184.804236] snd_pcm_oss: Unknown symbol snd_info_get_line
[25184.804390] snd_pcm_oss: Unknown symbol snd_pcm_format_width
[25309.898117] snd: Unknown symbol unregister_sound_special
[25309.898680] snd: Unknown symbol register_sound_special_device
[25309.899226] snd: Unknown symbol sound_class
[25309.972311] snd: Unknown symbol unregister_sound_special
[25309.972856] snd: Unknown symbol register_sound_special_device
[25309.973407] snd: Unknown symbol sound_class
[25310.047068] snd: Unknown symbol unregister_sound_special
[25310.047605] snd: Unknown symbol register_sound_special_device
[25310.048154] snd: Unknown symbol sound_class
[25310.122074] snd: Unknown symbol unregister_sound_special
[25310.122661] snd: Unknown symbol register_sound_special_device
[25310.123228] snd: Unknown symbol sound_class
[25310.195983] snd: Unknown symbol unregister_sound_special
[25310.196498] snd: Unknown symbol register_sound_special_device
[25310.197056] snd: Unknown symbol sound_class
[25310.271156] snd: Unknown symbol unregister_sound_special
[25310.271679] snd: Unknown symbol register_sound_special_device
[25310.272234] snd: Unknown symbol sound_class
[25310.346312] snd: Unknown symbol unregister_sound_special
[25310.346863] snd: Unknown symbol register_sound_special_device
[25310.347405] snd: Unknown symbol sound_class
[25310.422163] snd: Unknown symbol unregister_sound_special
[25310.422705] snd: Unknown symbol register_sound_special_device
[25310.423301] snd: Unknown symbol sound_class
[25314.648065] snd: Unknown symbol unregister_sound_special
[25314.648210] snd: Unknown symbol register_sound_special_device
[25314.648553] snd: Unknown symbol sound_class
[25314.722904] snd: Unknown symbol unregister_sound_special
[25314.723050] snd: Unknown symbol register_sound_special_device
[25314.723395] snd: Unknown symbol sound_class
[25314.805262] snd: Unknown symbol unregister_sound_special
[25314.805398] snd: Unknown symbol register_sound_special_device
[25314.805722] snd: Unknown symbol sound_class
[25314.880487] snd: Unknown symbol unregister_sound_special
[25314.880631] snd: Unknown symbol register_sound_special_device
[25314.880982] snd: Unknown symbol sound_class
[25314.956537] snd: Unknown symbol unregister_sound_special
[25314.956834] snd: Unknown symbol register_sound_special_device
[25314.957280] snd: Unknown symbol sound_class
[25315.036436] snd: Unknown symbol unregister_sound_special
[25315.036943] snd: Unknown symbol register_sound_special_device
[25315.037496] snd: Unknown symbol sound_class
[25315.114860] snd: Unknown symbol unregister_sound_special
[25315.115378] snd: Unknown symbol register_sound_special_device
[25315.116086] snd: Unknown symbol sound_class
[25315.199705] snd: Unknown symbol unregister_sound_special
[25315.200222] snd: Unknown symbol register_sound_special_device
[25315.200783] snd: Unknown symbol sound_class
[25315.274885] snd: Unknown symbol unregister_sound_special
[25315.275418] snd: Unknown symbol register_sound_special_device
[25315.275973] snd: Unknown symbol sound_class
[25315.349477] snd: Unknown symbol unregister_sound_special
[25315.350012] snd: Unknown symbol register_sound_special_device
[25315.350563] snd: Unknown symbol sound_class
[25315.425445] snd: Unknown symbol unregister_sound_special
[25315.425992] snd: Unknown symbol register_sound_special_device
[25315.426544] snd: Unknown symbol sound_class
[25315.502469] snd: Unknown symbol unregister_sound_special
[25315.503007] snd: Unknown symbol register_sound_special_device
[25315.503554] snd: Unknown symbol sound_class
[25315.576998] snd: Unknown symbol unregister_sound_special
[25315.577533] snd: Unknown symbol register_sound_special_device
[25315.578082] snd: Unknown symbol sound_class
[25315.650787] snd: Unknown symbol unregister_sound_special
[25315.651307] snd: Unknown symbol register_sound_special_device
[25315.651857] snd: Unknown symbol sound_class
[25315.727317] snd: Unknown symbol unregister_sound_special
[25315.727846] snd: Unknown symbol register_sound_special_device
[25315.728402] snd: Unknown symbol sound_class
[25315.802511] snd: Unknown symbol unregister_sound_special
[25315.803045] snd: Unknown symbol register_sound_special_device
[25315.803601] snd: Unknown symbol sound_class
[26365.069049] snd: Unknown symbol unregister_sound_special
[26365.069344] snd: Unknown symbol register_sound_special_device
[26365.070006] snd: Unknown symbol sound_class
[26365.071736] snd_seq_device: Unknown symbol snd_info_register
[26365.071929] snd_seq_device: Unknown symbol snd_info_create_module_entry
[26365.072108] snd_seq_device: Unknown symbol snd_info_free_entry
[26365.072283] snd_seq_device: Unknown symbol snd_seq_root
[26365.072449] snd_seq_device: Unknown symbol snd_verbose_printk
[26365.072611] snd_seq_device: Unknown symbol snd_iprintf
[26365.072776] snd_seq_device: Unknown symbol snd_device_new
[26365.074269] snd_rawmidi: Unknown symbol snd_info_register
[26365.074482] snd_rawmidi: Unknown symbol snd_seq_device_new
[26365.074645] snd_rawmidi: Unknown symbol snd_info_free_entry
[26365.074811] snd_rawmidi: Unknown symbol snd_unregister_oss_device
[26365.074990] snd_rawmidi: Unknown symbol snd_verbose_printk
[26365.075145] snd_rawmidi: Unknown symbol snd_register_oss_device
[26365.075319] snd_rawmidi: Unknown symbol snd_ctl_register_ioctl
[26365.075489] snd_rawmidi: Unknown symbol snd_card_file_add
[26365.075656] snd_rawmidi: Unknown symbol snd_iprintf
[26365.075809] snd_rawmidi: Unknown symbol snd_major
[26365.075972] snd_rawmidi: Unknown symbol snd_oss_info_register
[26365.076133] snd_rawmidi: Unknown symbol snd_unregister_device
[26365.076317] snd_rawmidi: Unknown symbol snd_device_new
[26365.076471] snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl
[26365.076658] snd_rawmidi: Unknown symbol snd_lookup_oss_minor_data
[26365.076833] snd_rawmidi: Unknown symbol snd_lookup_minor_data
[26365.076997] snd_rawmidi: Unknown symbol snd_info_create_card_entry
[26365.077178] snd_rawmidi: Unknown symbol snd_card_file_remove
[26365.077344] snd_rawmidi: Unknown symbol snd_register_device_for_dev
[26365.077644] snd_rawmidi: Unknown symbol snd_device_register
[26365.078851] snd_mpu401_uart: Unknown symbol snd_rawmidi_receive
[26365.079069] snd_mpu401_uart: Unknown symbol snd_verbose_printk
[26365.079245] snd_mpu401_uart: Unknown symbol snd_rawmidi_transmit_ack
[26365.079429] snd_mpu401_uart: Unknown symbol release_and_free_resource
[26365.079609] snd_mpu401_uart: Unknown symbol snd_rawmidi_transmit_peek
[26365.079787] snd_mpu401_uart: Unknown symbol snd_rawmidi_new
[26365.079955] snd_mpu401_uart: Unknown symbol snd_rawmidi_set_ops
[26365.080132] snd_mpu401_uart: Unknown symbol snd_device_free
[26365.081279] snd_i2c: Unknown symbol snd_device_new
[26365.081465] snd_i2c: Unknown symbol snd_device_free
[26365.082954] snd_timer: Unknown symbol snd_info_register
[26365.083148] snd_timer: Unknown symbol snd_info_create_module_entry
[26365.083335] snd_timer: Unknown symbol snd_info_free_entry
[26365.083829] snd_timer: Unknown symbol snd_verbose_printk
[26365.084000] snd_timer: Unknown symbol snd_iprintf
[26365.084168] snd_timer: Unknown symbol snd_ecards_limit
[26365.084339] snd_timer: Unknown symbol snd_oss_info_register
[26365.084504] snd_timer: Unknown symbol snd_unregister_device
[26365.084682] snd_timer: Unknown symbol snd_device_new
[26365.084873] snd_timer: Unknown symbol snd_register_device_for_dev
[26365.123591] snd: Unknown symbol unregister_sound_special
[26365.124334] snd: Unknown symbol register_sound_special_device
[26365.125026] snd: Unknown symbol sound_class
[26365.127027] snd_timer: Unknown symbol snd_info_register
[26365.127477] snd_timer: Unknown symbol snd_info_create_module_entry
[26365.127750] snd_timer: Unknown symbol snd_info_free_entry
[26365.128016] snd_timer: Unknown symbol snd_verbose_printk
[26365.128274] snd_timer: Unknown symbol snd_iprintf
[26365.128555] snd_timer: Unknown symbol snd_ecards_limit
[26365.128806] snd_timer: Unknown symbol snd_oss_info_register
[26365.129049] snd_timer: Unknown symbol snd_unregister_device
[26365.129324] snd_timer: Unknown symbol snd_device_new
[26365.129601] snd_timer: Unknown symbol snd_register_device_for_dev
[26365.133463] snd_pcm: Unknown symbol snd_info_register
[26365.133891] snd_pcm: Unknown symbol snd_info_create_module_entry
[26365.138921] snd_pcm: Unknown symbol snd_timer_notify
[26365.139514] snd_pcm: Unknown symbol snd_timer_interrupt
[26365.139768] snd_pcm: Unknown symbol snd_info_free_entry
[26365.140008] snd_pcm: Unknown symbol snd_add_device_sysfs_file
[26365.140281] snd_pcm: Unknown symbol snd_info_get_str
[26365.140597] snd_pcm: Unknown symbol snd_verbose_printk
[26365.140885] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[26365.141138] snd_pcm: Unknown symbol snd_card_file_add
[26365.141391] snd_pcm: Unknown symbol snd_iprintf
[26365.141650] snd_pcm: Unknown symbol snd_major
[26365.141923] snd_pcm: Unknown symbol snd_unregister_device
[26365.142187] snd_pcm: Unknown symbol snd_timer_new
[26365.142417] snd_pcm: Unknown symbol snd_device_new
[26365.142671] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[26365.142954] snd_pcm: Unknown symbol snd_lookup_minor_data
[26365.143216] snd_pcm: Unknown symbol snd_info_create_card_entry
[26365.143478] snd_pcm: Unknown symbol snd_power_wait
[26365.143716] snd_pcm: Unknown symbol snd_device_free
[26365.143969] snd_pcm: Unknown symbol snd_card_file_remove
[26365.144214] snd_pcm: Unknown symbol snd_register_device_for_dev
[26365.144526] snd_pcm: Unknown symbol snd_device_register
[26365.144766] snd_pcm: Unknown symbol snd_info_get_line
[26365.148387] snd_ac97_codec: Unknown symbol snd_info_register
[26365.148807] snd_ac97_codec: Unknown symbol snd_ctl_add
[26365.149101] snd_ac97_codec: Unknown symbol snd_info_free_entry
[26365.155604] snd_ac97_codec: Unknown symbol snd_interval_refine
[26365.155927] snd_ac97_codec: Unknown symbol snd_ctl_find_id
[26365.156190] snd_ac97_codec: Unknown symbol snd_verbose_printk
[26365.156570] snd_ac97_codec: Unknown symbol snd_ctl_new1
[26365.156821] snd_ac97_codec: Unknown symbol snd_ctl_remove_id
[26365.157091] snd_ac97_codec: Unknown symbol snd_component_add
[26365.157347] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[26365.157599] snd_ac97_codec: Unknown symbol snd_iprintf
[26365.157899] snd_ac97_codec: Unknown symbol snd_device_new
[26365.158183] snd_ac97_codec: Unknown symbol snd_info_create_card_entry
[26365.159738] snd_cs8427: Unknown symbol snd_ctl_add
[26365.160142] snd_cs8427: Unknown symbol snd_verbose_printk
[26365.160409] snd_cs8427: Unknown symbol snd_ctl_new1
[26365.160640] snd_cs8427: Unknown symbol snd_i2c_readbytes
[26365.160883] snd_cs8427: Unknown symbol snd_i2c_device_free
[26365.161132] snd_cs8427: Unknown symbol snd_ctl_notify
[26365.161636] snd_cs8427: Unknown symbol snd_i2c_sendbytes
[26365.161929] snd_cs8427: Unknown symbol snd_i2c_device_create
[26365.163205] snd_ak4xxx_adda: Unknown symbol snd_ctl_add
[26365.163608] snd_ak4xxx_adda: Unknown symbol snd_ctl_new1
[26365.164907] snd_ice17xx_ak4xxx: Unknown symbol snd_akm4xxx_init
[26365.165367] snd_ice17xx_ak4xxx: Unknown symbol snd_akm4xxx_build_controls
[26365.168507] snd_ice1712: Unknown symbol snd_ice1712_akm4xxx_init
[26365.168968] snd_ice1712: Unknown symbol snd_ctl_add
[26365.169229] snd_ice1712: Unknown symbol snd_pcm_new
[26365.169481] snd_ice1712: Unknown symbol snd_card_register
[26365.169724] snd_ice1712: Unknown symbol snd_card_free
[26365.169955] snd_ice1712: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[26365.170450] snd_ice1712: Unknown symbol snd_card_proc_new
[26365.170745] snd_ice1712: Unknown symbol snd_akm4xxx_write
[26365.170998] snd_ice1712: Unknown symbol snd_cs8427_iec958_active
[26365.171297] snd_ice1712: Unknown symbol snd_ac97_set_rate
[26365.171561] snd_ice1712: Unknown symbol snd_ac97_mixer
[26365.171804] snd_ice1712: Unknown symbol snd_ac97_bus
[26365.172044] snd_ice1712: Unknown symbol snd_pcm_set_sync
[26365.172305] snd_ice1712: Unknown symbol snd_verbose_printk
[26365.172552] snd_ice1712: Unknown symbol snd_cs8427_iec958_pcm
[26365.172802] snd_ice1712: Unknown symbol snd_ctl_new1
[26365.173050] snd_ice1712: Unknown symbol snd_i2c_readbytes
[26365.173311] snd_ice1712: Unknown symbol snd_i2c_bus_create
[26365.173562] snd_ice1712: Unknown symbol snd_ice1712_akm4xxx_free
[26365.173856] snd_ice1712: Unknown symbol snd_cs8427_create
[26365.174110] snd_ice1712: Unknown symbol snd_card_new
[26365.174353] snd_ice1712: Unknown symbol snd_iprintf
[26365.174591] snd_ice1712: Unknown symbol snd_pcm_lib_malloc_pages
[26365.174852] snd_ice1712: Unknown symbol snd_pcm_lib_ioctl
[26365.175107] snd_ice1712: Unknown symbol snd_pcm_lib_free_pages
[26365.175366] snd_ice1712: Unknown symbol snd_cs8427_iec958_build
[26365.175620] snd_ice1712: Unknown symbol snd_akm4xxx_reset
[26365.175870] snd_ice1712: Unknown symbol snd_ctl_notify
[26365.176117] snd_ice1712: Unknown symbol snd_pcm_set_ops
[26365.176377] snd_ice1712: Unknown symbol snd_pcm_hw_constraint_list
[26365.176649] snd_ice1712: Unknown symbol snd_device_new
[26365.176887] snd_ice1712: Unknown symbol snd_cs8427_reg_write
[26365.177141] snd_ice1712: Unknown symbol snd_mpu401_uart_interrupt
[26365.177466] snd_ice1712: Unknown symbol snd_i2c_sendbytes
[26365.177714] snd_ice1712: Unknown symbol snd_ice1712_akm4xxx_build_controls
[26365.177997] snd_ice1712: Unknown symbol snd_mpu401_uart_new
[26365.178282] snd_ice1712: Unknown symbol snd_pcm_hw_constraint_msbits
[26365.178559] snd_ice1712: Unknown symbol snd_i2c_device_create
[26365.178811] snd_ice1712: Unknown symbol snd_pcm_period_elapsed
[26365.179074] snd_ice1712: Unknown symbol snd_pcm_format_width

Could anyone tell me what might be going on?

Thanks,
John

---

### Post by johnapeterson on 2007-08-19
Further info.

My kernel is:
2.6.20-16-lowlatency

Any idea on what to do?

Thanks

---

