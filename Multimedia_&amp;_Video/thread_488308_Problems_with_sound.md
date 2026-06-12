---
title: "Problems with sound"
date: 2007-06-30
forum: Multimedia &amp; Video
---

### Post by NobleSavage on 2007-06-30
I have a Creative Labs SB Audigy LS sound card it was working fine, but after a kernel update it quit working.  I'm using LTS.  

From the ALSA page I think I'm suposed to be usign module snd_ca0106

Modprobe give the following:
```

noble@noble:~$ sudo modprobe snd_ca0106
Password:
WARNING: Error inserting snd_timer (/lib/modules/2.6.15-28-386/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.15-28-386/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.15-28-386/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.15-28-386/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.15-28-386/kernel/sound/core/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.15-28-386/kernel/sound/core/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ca0106 (/lib/modules/2.6.15-28-386/kernel/sound/pci/ca0106/snd-ca0106.ko): Unknown symbol in module, or unknown parameter (see dmesg)
noble@noble:~$

```

dmseg
```



[17179586.136000] snd_intel8x0: Unknown symbol snd_ac97_update_bits
[17179586.136000] snd_intel8x0: Unknown symbol snd_ac97_mixer
[17179586.140000] snd_intel8x0: Unknown symbol snd_card_pci_resume
[17179586.140000] snd_intel8x0: Unknown symbol snd_ac97_bus
[17179586.140000] snd_intel8x0: Unknown symbol snd_ac97_pcm_double_rate_rules
[17179586.140000] snd_intel8x0: disagrees about version of symbol snd_card_new
[17179586.140000] snd_intel8x0: Unknown symbol snd_card_new
[17179586.140000] snd_intel8x0: Unknown symbol snd_ac97_suspend
[17179586.140000] snd_intel8x0: disagrees about version of symbol snd_iprintf
[17179586.140000] snd_intel8x0: Unknown symbol snd_iprintf
[17179586.140000] snd_intel8x0: Unknown symbol snd_pcm_lib_malloc_pages
[17179586.140000] snd_intel8x0: Unknown symbol snd_pcm_lib_ioctl
[17179586.140000] snd_intel8x0: Unknown symbol snd_pcm_lib_free_pages
[17179586.140000] snd_intel8x0: Unknown symbol snd_card_pci_suspend
[17179586.140000] snd_intel8x0: Unknown symbol snd_pcm_set_ops
[17179586.140000] snd_intel8x0: Unknown symbol snd_card_set_pm_callback
[17179586.140000] snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_list
[17179586.140000] snd_intel8x0: disagrees about version of symbol snd_device_new
[17179586.140000] snd_intel8x0: Unknown symbol snd_device_new
[17179586.140000] snd_intel8x0: Unknown symbol snd_ac97_get_short_name
[17179586.140000] snd_intel8x0: Unknown symbol snd_pcm_suspend_all
[17179586.140000] snd_intel8x0: Unknown symbol snd_ac97_pcm_assign
[17179586.140000] snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_integer
[17179586.140000] snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_msbits
[17179586.140000] snd_intel8x0: Unknown symbol snd_pcm_period_elapsed
[17179586.140000] snd_intel8x0: Unknown symbol snd_ac97_tune_hardware
[17179586.160000] parport: PnPBIOS parport detected.
[17179586.160000] parport0: PC-style at 0x378, irq 7 [PCSPP]
[17179586.604000] hw_random: RNG not detected
[17179586.624000] SCSI subsystem initialized
[17179586.664000] Initializing USB Mass Storage driver...
[17179586.664000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179586.664000] usb-storage: device found at 2
[17179586.664000] usb-storage: waiting for device to settle before scanning
[17179586.664000] usbcore: registered new driver usb-storage
[17179586.664000] USB Mass Storage support registered.
[17179586.680000] snd_timer: disagrees about version of symbol snd_info_register
[17179586.680000] snd_timer: Unknown symbol snd_info_register
[17179586.680000] snd_timer: disagrees about version of symbol snd_info_create_module_entry
[17179586.680000] snd_timer: Unknown symbol snd_info_create_module_entry
[17179586.680000] snd_timer: disagrees about version of symbol snd_info_free_entry
[17179586.680000] snd_timer: Unknown symbol snd_info_free_entry
[17179586.680000] snd_timer: disagrees about version of symbol snd_iprintf
[17179586.680000] snd_timer: Unknown symbol snd_iprintf
[17179586.680000] snd_timer: disagrees about version of symbol snd_unregister_device
[17179586.680000] snd_timer: Unknown symbol snd_unregister_device
[17179586.680000] snd_timer: disagrees about version of symbol snd_device_new
[17179586.680000] snd_timer: Unknown symbol snd_device_new
[17179586.680000] snd_timer: Unknown symbol snd_info_unregister
[17179586.680000] snd_timer: Unknown symbol snd_register_device
[17179586.684000] snd_timer: disagrees about version of symbol snd_info_register
[17179586.684000] snd_timer: Unknown symbol snd_info_register
[17179586.684000] snd_timer: disagrees about version of symbol snd_info_create_module_entry
[17179586.684000] snd_timer: Unknown symbol snd_info_create_module_entry
[17179586.684000] snd_timer: disagrees about version of symbol snd_info_free_entry
[17179586.684000] snd_timer: Unknown symbol snd_info_free_entry
[17179586.684000] snd_timer: disagrees about version of symbol snd_iprintf
[17179586.684000] snd_timer: Unknown symbol snd_iprintf
[17179586.684000] snd_timer: disagrees about version of symbol snd_unregister_device
[17179586.684000] snd_timer: Unknown symbol snd_unregister_device
[17179586.684000] snd_timer: disagrees about version of symbol snd_device_new
[17179586.684000] snd_timer: Unknown symbol snd_device_new
[17179586.684000] snd_timer: Unknown symbol snd_info_unregister
[17179586.684000] snd_timer: Unknown symbol snd_register_device
[17179586.684000] snd_pcm: Unknown symbol snd_timer_notify
[17179586.684000] snd_pcm: Unknown symbol snd_timer_interrupt
[17179586.684000] snd_pcm: Unknown symbol snd_timer_new
[17179586.688000] snd_ac97_codec: disagrees about version of symbol snd_info_register
[17179586.688000] snd_ac97_codec: Unknown symbol snd_info_register
[17179586.688000] snd_ac97_codec: disagrees about version of symbol snd_ctl_add
[17179586.688000] snd_ac97_codec: Unknown symbol snd_ctl_add
[17179586.688000] snd_ac97_codec: disagrees about version of symbol snd_info_free_entry
[17179586.688000] snd_ac97_codec: Unknown symbol snd_info_free_entry
[17179586.688000] snd_ac97_codec: Unknown symbol snd_interval_refine
[17179586.688000] snd_ac97_codec: disagrees about version of symbol snd_ctl_find_id
[17179586.688000] snd_ac97_codec: Unknown symbol snd_ctl_find_id
[17179586.688000] snd_ac97_codec: disagrees about version of symbol snd_ctl_new1
[17179586.688000] snd_ac97_codec: Unknown symbol snd_ctl_new1
[17179586.688000] snd_ac97_codec: disagrees about version of symbol snd_ctl_remove_id
[17179586.688000] snd_ac97_codec: Unknown symbol snd_ctl_remove_id
[17179586.688000] snd_ac97_codec: disagrees about version of symbol snd_component_add
[17179586.688000] snd_ac97_codec: Unknown symbol snd_component_add
[17179586.688000] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[17179586.688000] snd_ac97_codec: disagrees about version of symbol snd_iprintf
[17179586.688000] snd_ac97_codec: Unknown symbol snd_iprintf
[17179586.688000] snd_ac97_codec: disagrees about version of symbol snd_device_new
[17179586.688000] snd_ac97_codec: Unknown symbol snd_device_new
[17179586.688000] snd_ac97_codec: disagrees about version of symbol snd_info_create_card_entry
[17179586.688000] snd_ac97_codec: Unknown symbol snd_info_create_card_entry
[17179586.688000] snd_ac97_codec: Unknown symbol snd_info_unregister
[17179586.772000] 8139too Fast Ethernet driver 0.9.27
[17179586.772000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 201
[17179586.772000] eth0: RealTek RTL8139 at 0xf8918f00, 00:16:17:4a:8f:bf, IRQ 201
[17179586.772000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179586.776000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179586.792000] snd_seq_device: disagrees about version of symbol snd_info_register
[17179586.792000] snd_seq_device: Unknown symbol snd_info_register
[17179586.792000] snd_seq_device: disagrees about version of symbol snd_info_create_module_entry
[17179586.792000] snd_seq_device: Unknown symbol snd_info_create_module_entry
[17179586.792000] snd_seq_device: disagrees about version of symbol snd_info_free_entry
[17179586.792000] snd_seq_device: Unknown symbol snd_info_free_entry
[17179586.792000] snd_seq_device: disagrees about version of symbol snd_seq_root
[17179586.792000] snd_seq_device: Unknown symbol snd_seq_root
[17179586.792000] snd_seq_device: disagrees about version of symbol snd_iprintf
[17179586.792000] snd_seq_device: Unknown symbol snd_iprintf
[17179586.792000] snd_seq_device: disagrees about version of symbol snd_device_new
[17179586.792000] snd_seq_device: Unknown symbol snd_device_new
[17179586.792000] snd_seq_device: Unknown symbol snd_info_unregister
[17179586.800000] snd_rawmidi: disagrees about version of symbol snd_info_register
[17179586.800000] snd_rawmidi: Unknown symbol snd_info_register
[17179586.800000] snd_rawmidi: Unknown symbol snd_seq_device_new
[17179586.800000] snd_rawmidi: disagrees about version of symbol snd_info_free_entry
[17179586.800000] snd_rawmidi: Unknown symbol snd_info_free_entry
[17179586.800000] snd_rawmidi: disagrees about version of symbol snd_unregister_oss_device
[17179586.800000] snd_rawmidi: Unknown symbol snd_unregister_oss_device
[17179586.800000] snd_rawmidi: disagrees about version of symbol snd_register_oss_device
[17179586.800000] snd_rawmidi: Unknown symbol snd_register_oss_device
[17179586.800000] snd_rawmidi: disagrees about version of symbol snd_ctl_register_ioctl
[17179586.800000] snd_rawmidi: Unknown symbol snd_ctl_register_ioctl
[17179586.800000] snd_rawmidi: disagrees about version of symbol snd_card_file_add
[17179586.800000] snd_rawmidi: Unknown symbol snd_card_file_add
[17179586.800000] snd_rawmidi: disagrees about version of symbol snd_iprintf
[17179586.800000] snd_rawmidi: Unknown symbol snd_iprintf
[17179586.800000] snd_rawmidi: disagrees about version of symbol snd_unregister_device
[17179586.800000] snd_rawmidi: Unknown symbol snd_unregister_device
[17179586.800000] snd_rawmidi: disagrees about version of symbol snd_device_new
[17179586.800000] snd_rawmidi: Unknown symbol snd_device_new
[17179586.800000] snd_rawmidi: disagrees about version of symbol snd_ctl_unregister_ioctl
[17179586.800000] snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl
[17179586.800000] snd_rawmidi: disagrees about version of symbol snd_info_create_card_entry
[17179586.800000] snd_rawmidi: Unknown symbol snd_info_create_card_entry
[17179586.800000] snd_rawmidi: disagrees about version of symbol snd_device_free
[17179586.800000] snd_rawmidi: Unknown symbol snd_device_free
[17179586.800000] snd_rawmidi: disagrees about version of symbol snd_card_file_remove
[17179586.800000] snd_rawmidi: Unknown symbol snd_card_file_remove
[17179586.800000] snd_rawmidi: Unknown symbol snd_info_unregister
[17179586.800000] snd_rawmidi: disagrees about version of symbol snd_device_register
[17179586.800000] snd_rawmidi: Unknown symbol snd_device_register
[17179586.800000] snd_rawmidi: Unknown symbol snd_register_device
[17179586.804000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179586.832000] snd_ca0106: Unknown symbol snd_rawmidi_receive
[17179586.832000] snd_ca0106: Unknown symbol snd_rawmidi_transmit
[17179586.832000] snd_ca0106: disagrees about version of symbol snd_ctl_add
[17179586.832000] snd_ca0106: Unknown symbol snd_ctl_add
[17179586.832000] snd_ca0106: Unknown symbol snd_pcm_new
[17179586.832000] snd_ca0106: disagrees about version of symbol snd_card_register
[17179586.832000] snd_ca0106: Unknown symbol snd_card_register
[17179586.832000] snd_ca0106: disagrees about version of symbol snd_card_free
[17179586.832000] snd_ca0106: Unknown symbol snd_card_free
[17179586.832000] snd_ca0106: disagrees about version of symbol snd_card_proc_new
[17179586.832000] snd_ca0106: Unknown symbol snd_card_proc_new
[17179586.832000] snd_ca0106: Unknown symbol snd_ac97_mixer
[17179586.832000] snd_ca0106: Unknown symbol snd_ac97_bus
[17179586.832000] snd_ca0106: disagrees about version of symbol snd_ctl_find_id
[17179586.832000] snd_ca0106: Unknown symbol snd_ctl_find_id
[17179586.832000] snd_ca0106: disagrees about version of symbol snd_ctl_new1
[17179586.832000] snd_ca0106: Unknown symbol snd_ctl_new1
[17179586.832000] snd_ca0106: disagrees about version of symbol snd_ctl_remove_id
[17179586.832000] snd_ca0106: Unknown symbol snd_ctl_remove_id
[17179586.832000] snd_ca0106: disagrees about version of symbol snd_card_new
[17179586.832000] snd_ca0106: Unknown symbol snd_card_new
[17179586.832000] snd_ca0106: disagrees about version of symbol snd_iprintf
[17179586.832000] snd_ca0106: Unknown symbol snd_iprintf
[17179586.832000] snd_ca0106: Unknown symbol snd_pcm_lib_malloc_pages
[17179586.832000] snd_ca0106: Unknown symbol snd_pcm_lib_ioctl
[17179586.832000] snd_ca0106: Unknown symbol snd_pcm_lib_free_pages
[17179586.832000] snd_ca0106: Unknown symbol snd_pcm_set_ops
[17179586.832000] snd_ca0106: disagrees about version of symbol snd_device_new
[17179586.832000] snd_ca0106: Unknown symbol snd_device_new
[17179586.832000] snd_ca0106: Unknown symbol snd_rawmidi_new
[17179586.832000] snd_ca0106: Unknown symbol snd_pcm_hw_constraint_integer
[17179586.832000] snd_ca0106: Unknown symbol snd_rawmidi_set_ops
[17179586.832000] snd_ca0106: Unknown symbol snd_pcm_lib_preallocate_pages
[17179586.832000] snd_ca0106: Unknown symbol snd_pcm_lib_preallocate_free_for_all
[17179586.832000] snd_ca0106: Unknown symbol snd_pcm_period_elapsed
[17179586.832000] snd_ca0106: Unknown symbol snd_pcm_hw_constraint_step
[17179586.832000] snd_ca0106: disagrees about version of symbol snd_info_get_line
[17179586.832000] snd_ca0106: Unknown symbol snd_info_get_line
[17179587.132000] lp0: using parport0 (interrupt-driven).
[17179587.172000] Adding 1020056k swap on /dev/hda5.  Priority:-1 extents:1 across:1020056k
[17179587.172000] Adding 1020056k swap on /dev/hdb5.  Priority:-2 extents:1 across:1020056k
[17179587.304000] EXT3 FS on hda6, internal journal
[17179587.480000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179587.480000] md: bitmap version 4.39
[17179587.924000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179588.652000] cdrom: open failed.
[17179589.368000] kjournald starting.  Commit interval 5 seconds
[17179589.384000] EXT3 FS on hdb6, internal journal
[17179589.384000] EXT3-fs: mounted filesystem with ordered data mode.
[17179589.396000] NET: Registered protocol family 10
[17179589.396000] lo: Disabled Privacy Extensions
[17179589.396000] IPv6 over IPv4 tunneling driver
[17179591.192000] NET: Registered protocol family 17
[17179591.664000]   Vendor: USB 2.0   Model: Storage Device    Rev: 0100
[17179591.664000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179591.664000] usb-storage: device scan complete
[17179591.704000] Driver 'sd' needs updating - please use bus_type methods
[17179591.712000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[17179591.712000] sda: assuming drive cache: write through
[17179591.724000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[17179591.724000] sda: assuming drive cache: write through
[17179591.724000]  sda: sda1
[17179591.736000] sd 0:0:0:0: Attached scsi disk sda
[17179591.748000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179595.324000] ACPI: Power Button (FF) [PWRF]
[17179595.324000] ACPI: Power Button (CM) [PWRB]
[17179595.396000] ibm_acpi: ec object not found
[17179595.420000] pcc_acpi: loading...
[17179599.668000] eth0: no IPv6 routers present
[17179602.956000] ppdev: user-space parallel port driver
[17179603.732000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179603.732000] apm: overridden by ACPI.
[17179610.396000] Bluetooth: Core ver 2.8
[17179610.396000] NET: Registered protocol family 31
[17179610.396000] Bluetooth: HCI device and connection manager initialized
[17179610.396000] Bluetooth: HCI socket layer initialized
[17179610.444000] Bluetooth: L2CAP ver 2.8
[17179610.444000] Bluetooth: L2CAP socket layer initialized
[17179610.568000] Bluetooth: RFCOMM socket layer initialized
[17179610.568000] Bluetooth: RFCOMM TTY layer initialized
[17179610.568000] Bluetooth: RFCOMM ver 1.7
[17179635.532000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17498186.876000] ibm_acpi: ec object not found
[18103056.328000] ibm_acpi: ec object not found
[18707711.932000] ibm_acpi: ec object not found
[18858724.368000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[18858734.576000] eth0: no IPv6 routers present
[19192741.264000] snd_timer: disagrees about version of symbol snd_info_register
[19192741.264000] snd_timer: Unknown symbol snd_info_register
[19192741.264000] snd_timer: disagrees about version of symbol snd_info_create_module_entry
[19192741.264000] snd_timer: Unknown symbol snd_info_create_module_entry
[19192741.264000] snd_timer: disagrees about version of symbol snd_info_free_entry
[19192741.264000] snd_timer: Unknown symbol snd_info_free_entry
[19192741.264000] snd_timer: disagrees about version of symbol snd_iprintf
[19192741.264000] snd_timer: Unknown symbol snd_iprintf
[19192741.264000] snd_timer: disagrees about version of symbol snd_unregister_device
[19192741.264000] snd_timer: Unknown symbol snd_unregister_device
[19192741.264000] snd_timer: disagrees about version of symbol snd_device_new
[19192741.264000] snd_timer: Unknown symbol snd_device_new
[19192741.264000] snd_timer: Unknown symbol snd_info_unregister
[19192741.264000] snd_timer: Unknown symbol snd_register_device
[19192741.272000] snd_timer: disagrees about version of symbol snd_info_register
[19192741.272000] snd_timer: Unknown symbol snd_info_register
[19192741.272000] snd_timer: disagrees about version of symbol snd_info_create_module_entry
[19192741.272000] snd_timer: Unknown symbol snd_info_create_module_entry
[19192741.272000] snd_timer: disagrees about version of symbol snd_info_free_entry
[19192741.272000] snd_timer: Unknown symbol snd_info_free_entry
[19192741.272000] snd_timer: disagrees about version of symbol snd_iprintf
[19192741.272000] snd_timer: Unknown symbol snd_iprintf
[19192741.272000] snd_timer: disagrees about version of symbol snd_unregister_device
[19192741.272000] snd_timer: Unknown symbol snd_unregister_device
[19192741.272000] snd_timer: disagrees about version of symbol snd_device_new
[19192741.272000] snd_timer: Unknown symbol snd_device_new
[19192741.272000] snd_timer: Unknown symbol snd_info_unregister
[19192741.272000] snd_timer: Unknown symbol snd_register_device
[19192741.276000] snd_pcm: Unknown symbol snd_timer_notify
[19192741.276000] snd_pcm: Unknown symbol snd_timer_interrupt
[19192741.276000] snd_pcm: Unknown symbol snd_timer_new
[19192741.276000] snd_ac97_codec: disagrees about version of symbol snd_info_register
[19192741.276000] snd_ac97_codec: Unknown symbol snd_info_register
[19192741.276000] snd_ac97_codec: disagrees about version of symbol snd_ctl_add
[19192741.276000] snd_ac97_codec: Unknown symbol snd_ctl_add
[19192741.276000] snd_ac97_codec: disagrees about version of symbol snd_info_free_entry
[19192741.276000] snd_ac97_codec: Unknown symbol snd_info_free_entry
[19192741.276000] snd_ac97_codec: Unknown symbol snd_interval_refine
[19192741.276000] snd_ac97_codec: disagrees about version of symbol snd_ctl_find_id
[19192741.276000] snd_ac97_codec: Unknown symbol snd_ctl_find_id
[19192741.276000] snd_ac97_codec: disagrees about version of symbol snd_ctl_new1
[19192741.276000] snd_ac97_codec: Unknown symbol snd_ctl_new1
[19192741.276000] snd_ac97_codec: disagrees about version of symbol snd_ctl_remove_id
[19192741.276000] snd_ac97_codec: Unknown symbol snd_ctl_remove_id
[19192741.276000] snd_ac97_codec: disagrees about version of symbol snd_component_add
[19192741.276000] snd_ac97_codec: Unknown symbol snd_component_add
[19192741.276000] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[19192741.276000] snd_ac97_codec: disagrees about version of symbol snd_iprintf
[19192741.276000] snd_ac97_codec: Unknown symbol snd_iprintf
[19192741.276000] snd_ac97_codec: disagrees about version of symbol snd_device_new
[19192741.276000] snd_ac97_codec: Unknown symbol snd_device_new
[19192741.276000] snd_ac97_codec: disagrees about version of symbol snd_info_create_card_entry
[19192741.276000] snd_ac97_codec: Unknown symbol snd_info_create_card_entry
[19192741.276000] snd_ac97_codec: Unknown symbol snd_info_unregister
[19192741.276000] snd_seq_device: disagrees about version of symbol snd_info_register
[19192741.276000] snd_seq_device: Unknown symbol snd_info_register
[19192741.276000] snd_seq_device: disagrees about version of symbol snd_info_create_module_entry
[19192741.276000] snd_seq_device: Unknown symbol snd_info_create_module_entry
[19192741.276000] snd_seq_device: disagrees about version of symbol snd_info_free_entry
[19192741.276000] snd_seq_device: Unknown symbol snd_info_free_entry
[19192741.276000] snd_seq_device: disagrees about version of symbol snd_seq_root
[19192741.276000] snd_seq_device: Unknown symbol snd_seq_root
[19192741.276000] snd_seq_device: disagrees about version of symbol snd_iprintf
[19192741.276000] snd_seq_device: Unknown symbol snd_iprintf
[19192741.276000] snd_seq_device: disagrees about version of symbol snd_device_new
[19192741.276000] snd_seq_device: Unknown symbol snd_device_new
[19192741.276000] snd_seq_device: Unknown symbol snd_info_unregister
[19192741.276000] snd_rawmidi: disagrees about version of symbol snd_info_register
[19192741.276000] snd_rawmidi: Unknown symbol snd_info_register
[19192741.276000] snd_rawmidi: Unknown symbol snd_seq_device_new
[19192741.276000] snd_rawmidi: disagrees about version of symbol snd_info_free_entry
[19192741.280000] snd_rawmidi: Unknown symbol snd_info_free_entry
[19192741.280000] snd_rawmidi: disagrees about version of symbol snd_unregister_oss_device
[19192741.280000] snd_rawmidi: Unknown symbol snd_unregister_oss_device
[19192741.280000] snd_rawmidi: disagrees about version of symbol snd_register_oss_device
[19192741.280000] snd_rawmidi: Unknown symbol snd_register_oss_device
[19192741.280000] snd_rawmidi: disagrees about version of symbol snd_ctl_register_ioctl
[19192741.280000] snd_rawmidi: Unknown symbol snd_ctl_register_ioctl
[19192741.280000] snd_rawmidi: disagrees about version of symbol snd_card_file_add
[19192741.280000] snd_rawmidi: Unknown symbol snd_card_file_add
[19192741.280000] snd_rawmidi: disagrees about version of symbol snd_iprintf
[19192741.280000] snd_rawmidi: Unknown symbol snd_iprintf
[19192741.280000] snd_rawmidi: disagrees about version of symbol snd_unregister_device
[19192741.280000] snd_rawmidi: Unknown symbol snd_unregister_device
[19192741.280000] snd_rawmidi: disagrees about version of symbol snd_device_new
[19192741.280000] snd_rawmidi: Unknown symbol snd_device_new
[19192741.280000] snd_rawmidi: disagrees about version of symbol snd_ctl_unregister_ioctl
[19192741.280000] snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl
[19192741.280000] snd_rawmidi: disagrees about version of symbol snd_info_create_card_entry
[19192741.280000] snd_rawmidi: Unknown symbol snd_info_create_card_entry
[19192741.280000] snd_rawmidi: disagrees about version of symbol snd_device_free
[19192741.280000] snd_rawmidi: Unknown symbol snd_device_free
[19192741.280000] snd_rawmidi: disagrees about version of symbol snd_card_file_remove
[19192741.280000] snd_rawmidi: Unknown symbol snd_card_file_remove
[19192741.280000] snd_rawmidi: Unknown symbol snd_info_unregister
[19192741.280000] snd_rawmidi: disagrees about version of symbol snd_device_register
[19192741.280000] snd_rawmidi: Unknown symbol snd_device_register
[19192741.280000] snd_rawmidi: Unknown symbol snd_register_device
[19192741.280000] snd_ca0106: Unknown symbol snd_rawmidi_receive
[19192741.280000] snd_ca0106: Unknown symbol snd_rawmidi_transmit
[19192741.280000] snd_ca0106: disagrees about version of symbol snd_ctl_add
[19192741.280000] snd_ca0106: Unknown symbol snd_ctl_add
[19192741.280000] snd_ca0106: Unknown symbol snd_pcm_new
[19192741.280000] snd_ca0106: disagrees about version of symbol snd_card_register
[19192741.280000] snd_ca0106: Unknown symbol snd_card_register
[19192741.280000] snd_ca0106: disagrees about version of symbol snd_card_free
[19192741.280000] snd_ca0106: Unknown symbol snd_card_free
[19192741.280000] snd_ca0106: disagrees about version of symbol snd_card_proc_new
[19192741.280000] snd_ca0106: Unknown symbol snd_card_proc_new
[19192741.280000] snd_ca0106: Unknown symbol snd_ac97_mixer
[19192741.280000] snd_ca0106: Unknown symbol snd_ac97_bus
[19192741.280000] snd_ca0106: disagrees about version of symbol snd_ctl_find_id
[19192741.280000] snd_ca0106: Unknown symbol snd_ctl_find_id
[19192741.280000] snd_ca0106: disagrees about version of symbol snd_ctl_new1
[19192741.280000] snd_ca0106: Unknown symbol snd_ctl_new1
[19192741.280000] snd_ca0106: disagrees about version of symbol snd_ctl_remove_id
[19192741.280000] snd_ca0106: Unknown symbol snd_ctl_remove_id
[19192741.280000] snd_ca0106: disagrees about version of symbol snd_card_new
[19192741.280000] snd_ca0106: Unknown symbol snd_card_new
[19192741.280000] snd_ca0106: disagrees about version of symbol snd_iprintf
[19192741.280000] snd_ca0106: Unknown symbol snd_iprintf
[19192741.280000] snd_ca0106: Unknown symbol snd_pcm_lib_malloc_pages
[19192741.280000] snd_ca0106: Unknown symbol snd_pcm_lib_ioctl
[19192741.280000] snd_ca0106: Unknown symbol snd_pcm_lib_free_pages
[19192741.280000] snd_ca0106: Unknown symbol snd_pcm_set_ops
[19192741.280000] snd_ca0106: disagrees about version of symbol snd_device_new
[19192741.280000] snd_ca0106: Unknown symbol snd_device_new
[19192741.280000] snd_ca0106: Unknown symbol snd_rawmidi_new
[19192741.280000] snd_ca0106: Unknown symbol snd_pcm_hw_constraint_integer
[19192741.280000] snd_ca0106: Unknown symbol snd_rawmidi_set_ops
[19192741.280000] snd_ca0106: Unknown symbol snd_pcm_lib_preallocate_pages
[19192741.280000] snd_ca0106: Unknown symbol snd_pcm_lib_preallocate_free_for_all
[19192741.280000] snd_ca0106: Unknown symbol snd_pcm_period_elapsed
[19192741.280000] snd_ca0106: Unknown symbol snd_pcm_hw_constraint_step
[19192741.280000] snd_ca0106: disagrees about version of symbol snd_info_get_line
[19192741.280000] snd_ca0106: Unknown symbol snd_info_get_line
[19201276.816000] snd_timer: disagrees about version of symbol snd_info_register
[19201276.816000] snd_timer: Unknown symbol snd_info_register
[19201276.816000] snd_timer: disagrees about version of symbol snd_info_create_module_entry
[19201276.816000] snd_timer: Unknown symbol snd_info_create_module_entry
[19201276.816000] snd_timer: disagrees about version of symbol snd_info_free_entry
[19201276.816000] snd_timer: Unknown symbol snd_info_free_entry
[19201276.816000] snd_timer: disagrees about version of symbol snd_iprintf
[19201276.816000] snd_timer: Unknown symbol snd_iprintf
[19201276.816000] snd_timer: disagrees about version of symbol snd_unregister_device
[19201276.816000] snd_timer: Unknown symbol snd_unregister_device
[19201276.816000] snd_timer: disagrees about version of symbol snd_device_new
[19201276.816000] snd_timer: Unknown symbol snd_device_new
[19201276.816000] snd_timer: Unknown symbol snd_info_unregister
[19201276.816000] snd_timer: Unknown symbol snd_register_device
[19201276.824000] snd_timer: disagrees about version of symbol snd_info_register
[19201276.824000] snd_timer: Unknown symbol snd_info_register
[19201276.824000] snd_timer: disagrees about version of symbol snd_info_create_module_entry
[19201276.824000] snd_timer: Unknown symbol snd_info_create_module_entry
[19201276.824000] snd_timer: disagrees about version of symbol snd_info_free_entry
[19201276.824000] snd_timer: Unknown symbol snd_info_free_entry
[19201276.824000] snd_timer: disagrees about version of symbol snd_iprintf
[19201276.824000] snd_timer: Unknown symbol snd_iprintf
[19201276.824000] snd_timer: disagrees about version of symbol snd_unregister_device
[19201276.824000] snd_timer: Unknown symbol snd_unregister_device
[19201276.824000] snd_timer: disagrees about version of symbol snd_device_new
[19201276.824000] snd_timer: Unknown symbol snd_device_new
[19201276.824000] snd_timer: Unknown symbol snd_info_unregister
[19201276.824000] snd_timer: Unknown symbol snd_register_device
[19201276.824000] snd_pcm: Unknown symbol snd_timer_notify
[19201276.824000] snd_pcm: Unknown symbol snd_timer_interrupt
[19201276.828000] snd_pcm: Unknown symbol snd_timer_new
[19201276.828000] snd_ac97_codec: disagrees about version of symbol snd_info_register
[19201276.828000] snd_ac97_codec: Unknown symbol snd_info_register
[19201276.828000] snd_ac97_codec: disagrees about version of symbol snd_ctl_add
[19201276.828000] snd_ac97_codec: Unknown symbol snd_ctl_add
[19201276.828000] snd_ac97_codec: disagrees about version of symbol snd_info_free_entry
[19201276.832000] snd_ac97_codec: Unknown symbol snd_info_free_entry
[19201276.832000] snd_ac97_codec: Unknown symbol snd_interval_refine
[19201276.832000] snd_ac97_codec: disagrees about version of symbol snd_ctl_find_id
[19201276.832000] snd_ac97_codec: Unknown symbol snd_ctl_find_id
[19201276.832000] snd_ac97_codec: disagrees about version of symbol snd_ctl_new1
[19201276.832000] snd_ac97_codec: Unknown symbol snd_ctl_new1
[19201276.832000] snd_ac97_codec: disagrees about version of symbol snd_ctl_remove_id
[19201276.832000] snd_ac97_codec: Unknown symbol snd_ctl_remove_id
[19201276.832000] snd_ac97_codec: disagrees about version of symbol snd_component_add
[19201276.832000] snd_ac97_codec: Unknown symbol snd_component_add
[19201276.832000] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[19201276.832000] snd_ac97_codec: disagrees about version of symbol snd_iprintf
[19201276.832000] snd_ac97_codec: Unknown symbol snd_iprintf
[19201276.832000] snd_ac97_codec: disagrees about version of symbol snd_device_new
[19201276.832000] snd_ac97_codec: Unknown symbol snd_device_new
[19201276.832000] snd_ac97_codec: disagrees about version of symbol snd_info_create_card_entry
[19201276.832000] snd_ac97_codec: Unknown symbol snd_info_create_card_entry
[19201276.832000] snd_ac97_codec: Unknown symbol snd_info_unregister
[19201276.832000] snd_seq_device: disagrees about version of symbol snd_info_register
[19201276.832000] snd_seq_device: Unknown symbol snd_info_register
[19201276.832000] snd_seq_device: disagrees about version of symbol snd_info_create_module_entry
[19201276.832000] snd_seq_device: Unknown symbol snd_info_create_module_entry
[19201276.832000] snd_seq_device: disagrees about version of symbol snd_info_free_entry
[19201276.832000] snd_seq_device: Unknown symbol snd_info_free_entry
[19201276.832000] snd_seq_device: disagrees about version of symbol snd_seq_root
[19201276.832000] snd_seq_device: Unknown symbol snd_seq_root
[19201276.832000] snd_seq_device: disagrees about version of symbol snd_iprintf
[19201276.832000] snd_seq_device: Unknown symbol snd_iprintf
[19201276.832000] snd_seq_device: disagrees about version of symbol snd_device_new
[19201276.832000] snd_seq_device: Unknown symbol snd_device_new
[19201276.832000] snd_seq_device: Unknown symbol snd_info_unregister
[19201276.832000] snd_rawmidi: disagrees about version of symbol snd_info_register
[19201276.832000] snd_rawmidi: Unknown symbol snd_info_register
[19201276.832000] snd_rawmidi: Unknown symbol snd_seq_device_new
[19201276.832000] snd_rawmidi: disagrees about version of symbol snd_info_free_entry
[19201276.832000] snd_rawmidi: Unknown symbol snd_info_free_entry
[19201276.832000] snd_rawmidi: disagrees about version of symbol snd_unregister_oss_device
[19201276.832000] snd_rawmidi: Unknown symbol snd_unregister_oss_device
[19201276.832000] snd_rawmidi: disagrees about version of symbol snd_register_oss_device
[19201276.836000] snd_rawmidi: Unknown symbol snd_register_oss_device
[19201276.836000] snd_rawmidi: disagrees about version of symbol snd_ctl_register_ioctl
[19201276.836000] snd_rawmidi: Unknown symbol snd_ctl_register_ioctl
[19201276.836000] snd_rawmidi: disagrees about version of symbol snd_card_file_add
[19201276.836000] snd_rawmidi: Unknown symbol snd_card_file_add
[19201276.836000] snd_rawmidi: disagrees about version of symbol snd_iprintf
[19201276.836000] snd_rawmidi: Unknown symbol snd_iprintf
[19201276.836000] snd_rawmidi: disagrees about version of symbol snd_unregister_device
[19201276.836000] snd_rawmidi: Unknown symbol snd_unregister_device
[19201276.836000] snd_rawmidi: disagrees about version of symbol snd_device_new
[19201276.836000] snd_rawmidi: Unknown symbol snd_device_new
[19201276.836000] snd_rawmidi: disagrees about version of symbol snd_ctl_unregister_ioctl
[19201276.836000] snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl
[19201276.836000] snd_rawmidi: disagrees about version of symbol snd_info_create_card_entry
[19201276.836000] snd_rawmidi: Unknown symbol snd_info_create_card_entry
[19201276.836000] snd_rawmidi: disagrees about version of symbol snd_device_free
[19201276.836000] snd_rawmidi: Unknown symbol snd_device_free
[19201276.836000] snd_rawmidi: disagrees about version of symbol snd_card_file_remove
[19201276.836000] snd_rawmidi: Unknown symbol snd_card_file_remove
[19201276.836000] snd_rawmidi: Unknown symbol snd_info_unregister
[19201276.836000] snd_rawmidi: disagrees about version of symbol snd_device_register
[19201276.836000] snd_rawmidi: Unknown symbol snd_device_register
[19201276.836000] snd_rawmidi: Unknown symbol snd_register_device
[19201276.988000] snd_ca0106: Unknown symbol snd_rawmidi_receive
[19201276.988000] snd_ca0106: Unknown symbol snd_rawmidi_transmit
[19201276.988000] snd_ca0106: disagrees about version of symbol snd_ctl_add
[19201276.988000] snd_ca0106: Unknown symbol snd_ctl_add
[19201276.988000] snd_ca0106: Unknown symbol snd_pcm_new
[19201276.988000] snd_ca0106: disagrees about version of symbol snd_card_register
[19201276.988000] snd_ca0106: Unknown symbol snd_card_register
[19201276.988000] snd_ca0106: disagrees about version of symbol snd_card_free
[19201276.988000] snd_ca0106: Unknown symbol snd_card_free
[19201276.988000] snd_ca0106: disagrees about version of symbol snd_card_proc_new
[19201276.988000] snd_ca0106: Unknown symbol snd_card_proc_new
[19201276.988000] snd_ca0106: Unknown symbol snd_ac97_mixer
[19201276.988000] snd_ca0106: Unknown symbol snd_ac97_bus
[19201276.988000] snd_ca0106: disagrees about version of symbol snd_ctl_find_id
[19201276.988000] snd_ca0106: Unknown symbol snd_ctl_find_id
[19201276.988000] snd_ca0106: disagrees about version of symbol snd_ctl_new1
[19201276.988000] snd_ca0106: Unknown symbol snd_ctl_new1
[19201276.988000] snd_ca0106: disagrees about version of symbol snd_ctl_remove_id
[19201276.988000] snd_ca0106: Unknown symbol snd_ctl_remove_id
[19201276.988000] snd_ca0106: disagrees about version of symbol snd_card_new
[19201276.988000] snd_ca0106: Unknown symbol snd_card_new
[19201276.988000] snd_ca0106: disagrees about version of symbol snd_iprintf
[19201276.988000] snd_ca0106: Unknown symbol snd_iprintf
[19201276.988000] snd_ca0106: Unknown symbol snd_pcm_lib_malloc_pages
[19201276.988000] snd_ca0106: Unknown symbol snd_pcm_lib_ioctl
[19201276.988000] snd_ca0106: Unknown symbol snd_pcm_lib_free_pages
[19201276.988000] snd_ca0106: Unknown symbol snd_pcm_set_ops
[19201276.988000] snd_ca0106: disagrees about version of symbol snd_device_new
[19201276.988000] snd_ca0106: Unknown symbol snd_device_new
[19201276.988000] snd_ca0106: Unknown symbol snd_rawmidi_new
[19201276.988000] snd_ca0106: Unknown symbol snd_pcm_hw_constraint_integer
[19201276.988000] snd_ca0106: Unknown symbol snd_rawmidi_set_ops
[19201276.988000] snd_ca0106: Unknown symbol snd_pcm_lib_preallocate_pages
[19201276.988000] snd_ca0106: Unknown symbol snd_pcm_lib_preallocate_free_for_all
[19201276.988000] snd_ca0106: Unknown symbol snd_pcm_period_elapsed
[19201276.988000] snd_ca0106: Unknown symbol snd_pcm_hw_constraint_step
[19201276.988000] snd_ca0106: disagrees about version of symbol snd_info_get_line
[19201276.988000] snd_ca0106: Unknown symbol snd_info_get_line

```

Any ideas?  I'm lost.

---

