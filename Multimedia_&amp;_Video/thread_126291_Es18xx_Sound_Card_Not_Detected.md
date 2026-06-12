---
title: "Es18xx Sound Card Not Detected"
date: 2006-02-06
forum: Multimedia &amp; Video
---

### Post by pracslipkerm on 2006-02-06
I have a ess1869 Sound Card. In the device manager the only field that comes up known is Bus Type = PnP. It is identified as PnP Device (Ess1869) in the device list.
When I try to run "sudo modprobe snd-es18xx" I get fatal errors as listed below with the ouput of dmesg and cat /proc/devices. I am getting way out of my depth? Should I try a reinstall (or is this just the MS habits coming back to haunt me). Any help would be very good. 
Cheers Steve :-)

root@Fred:/home/steve # modprobe snd-es18xx
FATAL: Error inserting snd (/lib/modules/2.6.10-5-386/kernel/sound/core/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.10-5-386/kernel/sound/core/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_mpu401_uart (/lib/modules/2.6.10-5-386/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_opl3_lib (/lib/modules/2.6.10-5-386/kernel/sound/drivers/opl3/snd-opl3-lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.10-5-386/kernel/sound/core/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
FATAL: Error inserting snd (/lib/modules/2.6.10-5-386/kernel/sound/core/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.10-5-386/kernel/sound/core/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_mpu401_uart (/lib/modules/2.6.10-5-386/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_opl3_lib (/lib/modules/2.6.10-5-386/kernel/sound/drivers/opl3/snd-opl3-lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.10-5-386/kernel/sound/core/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
FATAL: Error inserting snd_es18xx (/lib/modules/2.6.10-5-386/kernel/sound/isa/snd-es18xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for snd_es18xx
root@Fred:/home/steve #
root@Fred:/home/steve # dmesg
er
snd_hwdep: Unknown symbol snd_info_create_module_entry
snd_hwdep: Unknown symbol snd_info_free_entry
snd_hwdep: Unknown symbol snd_unregister_oss_device
snd_hwdep: Unknown symbol snd_register_oss_device
snd_hwdep: Unknown symbol snd_ctl_register_ioctl
snd_hwdep: Unknown symbol snd_card_file_add
snd_hwdep: Unknown symbol snd_iprintf
snd_hwdep: Unknown symbol snd_unregister_device
snd_hwdep: Unknown symbol snd_device_new
snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
snd_hwdep: Unknown symbol snd_card_file_remove
snd_hwdep: Unknown symbol snd_info_unregister
snd_hwdep: Unknown symbol snd_register_device
snd_timer: Unknown symbol snd_info_register
snd_timer: Unknown symbol snd_info_create_module_entry
snd_timer: Unknown symbol snd_info_free_entry
snd_timer: Unknown symbol snd_iprintf
snd_timer: Unknown symbol snd_ecards_limit
snd_timer: Unknown symbol snd_oss_info_register
snd_timer: Unknown symbol snd_unregister_device
snd_timer: Unknown symbol snd_device_new
snd_timer: Unknown symbol snd_kmalloc_strdup
snd_timer: Unknown symbol snd_info_unregister
snd_timer: Unknown symbol snd_register_device
snd_opl3_lib: Unknown symbol snd_seq_device_new
snd_opl3_lib: Unknown symbol snd_timer_interrupt
snd_opl3_lib: Unknown symbol snd_hwdep_new
snd_opl3_lib: Unknown symbol snd_timer_new
snd_opl3_lib: Unknown symbol snd_device_new
snd_opl3_lib: Unknown symbol snd_device_free
snd: Unknown parameter `es18xx'
snd_timer: Unknown symbol snd_info_register
snd_timer: Unknown symbol snd_info_create_module_entry
snd_timer: Unknown symbol snd_info_free_entry
snd_timer: Unknown symbol snd_iprintf
snd_timer: Unknown symbol snd_ecards_limit
snd_timer: Unknown symbol snd_oss_info_register
snd_timer: Unknown symbol snd_unregister_device
snd_timer: Unknown symbol snd_device_new
snd_timer: Unknown symbol snd_kmalloc_strdup
snd_timer: Unknown symbol snd_info_unregister
snd_timer: Unknown symbol snd_register_device
snd_pcm: Unknown symbol snd_info_register
snd_pcm: Unknown symbol snd_info_create_module_entry
snd_pcm: Unknown symbol snd_timer_notify
snd_pcm: Unknown symbol snd_timer_interrupt
snd_pcm: Unknown symbol snd_info_free_entry
snd_pcm: Unknown symbol snd_info_get_str
snd_pcm: Unknown symbol snd_ctl_register_ioctl
snd_pcm: Unknown symbol snd_card_file_add
snd_pcm: Unknown symbol snd_iprintf
snd_pcm: Unknown symbol snd_major
snd_pcm: Unknown symbol snd_unregister_device
snd_pcm: Unknown symbol snd_timer_new
snd_pcm: Unknown symbol snd_device_new
snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
snd_pcm: Unknown symbol snd_info_create_card_entry
snd_pcm: Unknown symbol snd_power_wait
snd_pcm: Unknown symbol snd_device_free
snd_pcm: Unknown symbol snd_card_file_remove
snd_pcm: Unknown symbol snd_info_unregister
snd_pcm: Unknown symbol snd_device_register
snd_pcm: Unknown symbol snd_register_device
snd_pcm: Unknown symbol snd_info_get_line
snd_es18xx: Unknown symbol snd_ctl_add
snd_es18xx: Unknown symbol snd_pcm_new
snd_es18xx: Unknown symbol snd_card_register
snd_es18xx: Unknown symbol snd_card_free
snd_es18xx: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
snd_es18xx: Unknown symbol snd_pcm_format_unsigned
snd_es18xx: Unknown symbol snd_opl3_create
snd_es18xx: Unknown symbol snd_dma_pointer
snd_es18xx: Unknown symbol snd_ctl_new1
snd_es18xx: Unknown symbol snd_card_new
snd_es18xx: Unknown symbol snd_pcm_lib_malloc_pages
snd_es18xx: Unknown symbol snd_pcm_lib_ioctl
snd_es18xx: Unknown symbol snd_pcm_lib_free_pages
snd_es18xx: Unknown symbol snd_ctl_notify
snd_es18xx: Unknown symbol snd_pcm_set_ops
snd_es18xx: Unknown symbol snd_device_new
snd_es18xx: Unknown symbol snd_mpu401_uart_interrupt
snd_es18xx: Unknown symbol snd_pcm_suspend_all
snd_es18xx: Unknown symbol snd_card_disconnect
snd_es18xx: Unknown symbol _snd_pcm_hw_param_setempty
snd_es18xx: Unknown symbol snd_mpu401_uart_new
snd_es18xx: Unknown symbol snd_card_free_in_thread
snd_es18xx: Unknown symbol snd_pcm_lib_preallocate_free_for_all
snd_es18xx: Unknown symbol snd_opl3_hwdep_new
snd_es18xx: Unknown symbol snd_pcm_hw_constraint_ratnums
snd_es18xx: Unknown symbol snd_pcm_period_elapsed
snd_es18xx: Unknown symbol snd_card_set_dev_pm_callback
snd_es18xx: Unknown symbol snd_dma_program
snd_es18xx: Unknown symbol snd_pcm_format_width
atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
snd: Unknown parameter `es18xx'
snd_seq_device: Unknown symbol snd_info_register
snd_seq_device: Unknown symbol snd_info_create_module_entry
snd_seq_device: Unknown symbol snd_info_free_entry
snd_seq_device: Unknown symbol snd_seq_root
snd_seq_device: Unknown symbol snd_iprintf
snd_seq_device: Unknown symbol snd_device_new
snd_seq_device: Unknown symbol snd_info_unregister
snd_rawmidi: Unknown symbol snd_info_register
snd_rawmidi: Unknown symbol snd_seq_device_new
snd_rawmidi: Unknown symbol snd_info_free_entry
snd_rawmidi: Unknown symbol snd_unregister_oss_device
snd_rawmidi: Unknown symbol snd_register_oss_device
snd_rawmidi: Unknown symbol snd_ctl_register_ioctl
snd_rawmidi: Unknown symbol snd_card_file_add
snd_rawmidi: Unknown symbol snd_iprintf
snd_rawmidi: Unknown symbol snd_oss_info_register
snd_rawmidi: Unknown symbol snd_unregister_device
snd_rawmidi: Unknown symbol snd_device_new
snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl
snd_rawmidi: Unknown symbol snd_info_create_card_entry
snd_rawmidi: Unknown symbol snd_device_free
snd_rawmidi: Unknown symbol snd_card_file_remove
snd_rawmidi: Unknown symbol snd_info_unregister
snd_rawmidi: Unknown symbol snd_device_register
snd_rawmidi: Unknown symbol snd_register_device
snd_mpu401_uart: Unknown symbol snd_rawmidi_receive
snd_mpu401_uart: Unknown symbol snd_rawmidi_transmit_ack
snd_mpu401_uart: Unknown symbol snd_rawmidi_transmit_peek
snd_mpu401_uart: Unknown symbol snd_rawmidi_new
snd_mpu401_uart: Unknown symbol snd_rawmidi_set_ops
snd_mpu401_uart: Unknown symbol snd_device_free
snd_hwdep: Unknown symbol snd_info_register
snd_hwdep: Unknown symbol snd_info_create_module_entry
snd_hwdep: Unknown symbol snd_info_free_entry
snd_hwdep: Unknown symbol snd_unregister_oss_device
snd_hwdep: Unknown symbol snd_register_oss_device
snd_hwdep: Unknown symbol snd_ctl_register_ioctl
snd_hwdep: Unknown symbol snd_card_file_add
snd_hwdep: Unknown symbol snd_iprintf
snd_hwdep: Unknown symbol snd_unregister_device
snd_hwdep: Unknown symbol snd_device_new
snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
snd_hwdep: Unknown symbol snd_card_file_remove
snd_hwdep: Unknown symbol snd_info_unregister
snd_hwdep: Unknown symbol snd_register_device
snd_timer: Unknown symbol snd_info_register
snd_timer: Unknown symbol snd_info_create_module_entry
snd_timer: Unknown symbol snd_info_free_entry
snd_timer: Unknown symbol snd_iprintf
snd_timer: Unknown symbol snd_ecards_limit
snd_timer: Unknown symbol snd_oss_info_register
snd_timer: Unknown symbol snd_unregister_device
snd_timer: Unknown symbol snd_device_new
snd_timer: Unknown symbol snd_kmalloc_strdup
snd_timer: Unknown symbol snd_info_unregister
snd_timer: Unknown symbol snd_register_device
snd_opl3_lib: Unknown symbol snd_seq_device_new
snd_opl3_lib: Unknown symbol snd_timer_interrupt
snd_opl3_lib: Unknown symbol snd_hwdep_new
snd_opl3_lib: Unknown symbol snd_timer_new
snd_opl3_lib: Unknown symbol snd_device_new
snd_opl3_lib: Unknown symbol snd_device_free
snd: Unknown parameter `es18xx'
snd_timer: Unknown symbol snd_info_register
snd_timer: Unknown symbol snd_info_create_module_entry
snd_timer: Unknown symbol snd_info_free_entry
snd_timer: Unknown symbol snd_iprintf
snd_timer: Unknown symbol snd_ecards_limit
snd_timer: Unknown symbol snd_oss_info_register
snd_timer: Unknown symbol snd_unregister_device
snd_timer: Unknown symbol snd_device_new
snd_timer: Unknown symbol snd_kmalloc_strdup
snd_timer: Unknown symbol snd_info_unregister
snd_timer: Unknown symbol snd_register_device
snd_pcm: Unknown symbol snd_info_register
snd_pcm: Unknown symbol snd_info_create_module_entry
snd_pcm: Unknown symbol snd_timer_notify
snd_pcm: Unknown symbol snd_timer_interrupt
snd_pcm: Unknown symbol snd_info_free_entry
snd_pcm: Unknown symbol snd_info_get_str
snd_pcm: Unknown symbol snd_ctl_register_ioctl
snd_pcm: Unknown symbol snd_card_file_add
snd_pcm: Unknown symbol snd_iprintf
snd_pcm: Unknown symbol snd_major
snd_pcm: Unknown symbol snd_unregister_device
snd_pcm: Unknown symbol snd_timer_new
snd_pcm: Unknown symbol snd_device_new
snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
snd_pcm: Unknown symbol snd_info_create_card_entry
snd_pcm: Unknown symbol snd_power_wait
snd_pcm: Unknown symbol snd_device_free
snd_pcm: Unknown symbol snd_card_file_remove
snd_pcm: Unknown symbol snd_info_unregister
snd_pcm: Unknown symbol snd_device_register
snd_pcm: Unknown symbol snd_register_device
snd_pcm: Unknown symbol snd_info_get_line
snd: Unknown parameter `es18xx'
snd_seq_device: Unknown symbol snd_info_register
snd_seq_device: Unknown symbol snd_info_create_module_entry
snd_seq_device: Unknown symbol snd_info_free_entry
snd_seq_device: Unknown symbol snd_seq_root
snd_seq_device: Unknown symbol snd_iprintf
snd_seq_device: Unknown symbol snd_device_new
snd_seq_device: Unknown symbol snd_info_unregister
snd_rawmidi: Unknown symbol snd_info_register
snd_rawmidi: Unknown symbol snd_seq_device_new
snd_rawmidi: Unknown symbol snd_info_free_entry
snd_rawmidi: Unknown symbol snd_unregister_oss_device
snd_rawmidi: Unknown symbol snd_register_oss_device
snd_rawmidi: Unknown symbol snd_ctl_register_ioctl
snd_rawmidi: Unknown symbol snd_card_file_add
snd_rawmidi: Unknown symbol snd_iprintf
snd_rawmidi: Unknown symbol snd_oss_info_register
snd_rawmidi: Unknown symbol snd_unregister_device
snd_rawmidi: Unknown symbol snd_device_new
snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl
snd_rawmidi: Unknown symbol snd_info_create_card_entry
snd_rawmidi: Unknown symbol snd_device_free
snd_rawmidi: Unknown symbol snd_card_file_remove
snd_rawmidi: Unknown symbol snd_info_unregister
snd_rawmidi: Unknown symbol snd_device_register
snd_rawmidi: Unknown symbol snd_register_device
snd_mpu401_uart: Unknown symbol snd_rawmidi_receive
snd_mpu401_uart: Unknown symbol snd_rawmidi_transmit_ack
snd_mpu401_uart: Unknown symbol snd_rawmidi_transmit_peek
snd_mpu401_uart: Unknown symbol snd_rawmidi_new
snd_mpu401_uart: Unknown symbol snd_rawmidi_set_ops
snd_mpu401_uart: Unknown symbol snd_device_free
snd_hwdep: Unknown symbol snd_info_register
snd_hwdep: Unknown symbol snd_info_create_module_entry
snd_hwdep: Unknown symbol snd_info_free_entry
snd_hwdep: Unknown symbol snd_unregister_oss_device
snd_hwdep: Unknown symbol snd_register_oss_device
snd_hwdep: Unknown symbol snd_ctl_register_ioctl
snd_hwdep: Unknown symbol snd_card_file_add
snd_hwdep: Unknown symbol snd_iprintf
snd_hwdep: Unknown symbol snd_unregister_device
snd_hwdep: Unknown symbol snd_device_new
snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
snd_hwdep: Unknown symbol snd_card_file_remove
snd_hwdep: Unknown symbol snd_info_unregister
snd_hwdep: Unknown symbol snd_register_device
snd_timer: Unknown symbol snd_info_register
snd_timer: Unknown symbol snd_info_create_module_entry
snd_timer: Unknown symbol snd_info_free_entry
snd_timer: Unknown symbol snd_iprintf
snd_timer: Unknown symbol snd_ecards_limit
snd_timer: Unknown symbol snd_oss_info_register
snd_timer: Unknown symbol snd_unregister_device
snd_timer: Unknown symbol snd_device_new
snd_timer: Unknown symbol snd_kmalloc_strdup
snd_timer: Unknown symbol snd_info_unregister
snd_timer: Unknown symbol snd_register_device
snd_opl3_lib: Unknown symbol snd_seq_device_new
snd_opl3_lib: Unknown symbol snd_timer_interrupt
snd_opl3_lib: Unknown symbol snd_hwdep_new
snd_opl3_lib: Unknown symbol snd_timer_new
snd_opl3_lib: Unknown symbol snd_device_new
snd_opl3_lib: Unknown symbol snd_device_free
snd: Unknown parameter `es18xx'
snd_timer: Unknown symbol snd_info_register
snd_timer: Unknown symbol snd_info_create_module_entry
snd_timer: Unknown symbol snd_info_free_entry
snd_timer: Unknown symbol snd_iprintf
snd_timer: Unknown symbol snd_ecards_limit
snd_timer: Unknown symbol snd_oss_info_register
snd_timer: Unknown symbol snd_unregister_device
snd_timer: Unknown symbol snd_device_new
snd_timer: Unknown symbol snd_kmalloc_strdup
snd_timer: Unknown symbol snd_info_unregister
snd_timer: Unknown symbol snd_register_device
snd_pcm: Unknown symbol snd_info_register
snd_pcm: Unknown symbol snd_info_create_module_entry
snd_pcm: Unknown symbol snd_timer_notify
snd_pcm: Unknown symbol snd_timer_interrupt
snd_pcm: Unknown symbol snd_info_free_entry
snd_pcm: Unknown symbol snd_info_get_str
snd_pcm: Unknown symbol snd_ctl_register_ioctl
snd_pcm: Unknown symbol snd_card_file_add
snd_pcm: Unknown symbol snd_iprintf
snd_pcm: Unknown symbol snd_major
snd_pcm: Unknown symbol snd_unregister_device
snd_pcm: Unknown symbol snd_timer_new
snd_pcm: Unknown symbol snd_device_new
snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
snd_pcm: Unknown symbol snd_info_create_card_entry
snd_pcm: Unknown symbol snd_power_wait
snd_pcm: Unknown symbol snd_device_free
snd_pcm: Unknown symbol snd_card_file_remove
snd_pcm: Unknown symbol snd_info_unregister
snd_pcm: Unknown symbol snd_device_register
snd_pcm: Unknown symbol snd_register_device
snd_pcm: Unknown symbol snd_info_get_line
snd_es18xx: Unknown symbol snd_ctl_add
snd_es18xx: Unknown symbol snd_pcm_new
snd_es18xx: Unknown symbol snd_card_register
snd_es18xx: Unknown symbol snd_card_free
snd_es18xx: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
snd_es18xx: Unknown symbol snd_pcm_format_unsigned
snd_es18xx: Unknown symbol snd_opl3_create
snd_es18xx: Unknown symbol snd_dma_pointer
snd_es18xx: Unknown symbol snd_ctl_new1
snd_es18xx: Unknown symbol snd_card_new
snd_es18xx: Unknown symbol snd_pcm_lib_malloc_pages
snd_es18xx: Unknown symbol snd_pcm_lib_ioctl
snd_es18xx: Unknown symbol snd_pcm_lib_free_pages
snd_es18xx: Unknown symbol snd_ctl_notify
snd_es18xx: Unknown symbol snd_pcm_set_ops
snd_es18xx: Unknown symbol snd_device_new
snd_es18xx: Unknown symbol snd_mpu401_uart_interrupt
snd_es18xx: Unknown symbol snd_pcm_suspend_all
snd_es18xx: Unknown symbol snd_card_disconnect
snd_es18xx: Unknown symbol _snd_pcm_hw_param_setempty
snd_es18xx: Unknown symbol snd_mpu401_uart_new
snd_es18xx: Unknown symbol snd_card_free_in_thread
snd_es18xx: Unknown symbol snd_pcm_lib_preallocate_free_for_all
snd_es18xx: Unknown symbol snd_opl3_hwdep_new
snd_es18xx: Unknown symbol snd_pcm_hw_constraint_ratnums
snd_es18xx: Unknown symbol snd_pcm_period_elapsed
snd_es18xx: Unknown symbol snd_card_set_dev_pm_callback
snd_es18xx: Unknown symbol snd_dma_program
snd_es18xx: Unknown symbol snd_pcm_format_width
atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
root@Fred:/home/steve # cat /proc/devices
Character devices:
  1 mem
  2 pty
  3 ttyp
  4 /dev/vc/0
  4 tty
  4 ttyS
  5 /dev/tty
  5 /dev/console
  5 /dev/ptmx
  6 lp
  7 vcs
 10 misc
 13 input
 14 sound
 29 fb
128 ptm
136 pts
180 usb
216 rfcomm
254 devfs

Block devices:
  1 ramdisk
  2 fd
  3 ide0
  8 sd
  9 md
 22 ide1
 65 sd
 66 sd
 67 sd
 68 sd
 69 sd
 70 sd
 71 sd
128 sd
129 sd
130 sd
131 sd
132 sd
133 sd
134 sd
135 sd
253 device-mapper
254 mdp

---

### Post by FarEast on 2006-02-06
Hi pracslipkerm,
I have helped wukkkie with the same problem you have.
[http://ubuntuforums.org/showthread.php?t=114493](http://ubuntuforums.org/showthread.php?t=114493)

I hope this help you, too :).

---

