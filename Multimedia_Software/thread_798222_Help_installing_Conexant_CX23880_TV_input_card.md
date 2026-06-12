---
title: "Help installing Conexant CX23880 TV input card"
date: 2008-05-18
forum: Multimedia Software
---

### Post by Geogriffith on 2008-05-18
Hello, first time posting on the forums. Most of my initial issues have been solved by googling or lurking, but I've recently hit up against a brick wall when it comes to installing a "Conexant CX23880" PCI tv tuner card.

I have the card physically installed, and a terminal prompt of "lspci" will give the following listing:
```
01:05.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
```

Various help sites have promised to solve all my woes, such as [[COLOR="Red"]this linuxtv.org page[/COLOR]](http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers) and others, but despite my following them to the letter, nothing appears to work. Compiling and installation seems to work, but after I reboot, this is all that I am getting:
```
griffith@griffith-dvr:~$ sudo modprobe -r cx8800
griffith@griffith-dvr:~$ sudo modprobe -r cx88xx
griffith@griffith-dvr:~$ sudo modprobe cx8800
WARNING: Error inserting cx88xx (/lib/modules/2.6.24-16-generic/ubuntu/media/cx88/cx88xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting cx8800 (/lib/modules/2.6.24-16-generic/ubuntu/media/cx88/cx8800.ko): Unknown symbol in module, or unknown parameter (see dmesg)
griffith@griffith-dvr:~$ sudo modprobe cx88xx
FATAL: Error inserting cx88xx (/lib/modules/2.6.24-16-generic/ubuntu/media/cx88/cx88xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

dmesg gives me this (trimmed to the most recent entries)
```
[ 1087.996429] cx8800: disagrees about version of symbol videobuf_streamoff
[ 1087.996436] cx8800: Unknown symbol videobuf_streamoff
[ 1087.996493] cx8800: Unknown symbol cx88_reset
[ 1087.996522] cx8800: disagrees about version of symbol videobuf_poll_stream
[ 1087.996525] cx8800: Unknown symbol videobuf_poll_stream
[ 1087.996580] cx8800: Unknown symbol cx88_call_i2c_clients
[ 1087.996613] cx8800: Unknown symbol cx88_wakeup
[ 1087.996654] cx8800: Unknown symbol cx88_risc_stopper
[ 1087.996716] cx8800: Unknown symbol cx88_print_irqbits
[ 1087.996749] cx8800: Unknown symbol cx88_set_scale
[ 1087.996790] cx8800: Unknown symbol cx88_shutdown
[ 1087.996818] cx8800: disagrees about version of symbol videobuf_reqbufs
[ 1087.996820] cx8800: Unknown symbol videobuf_reqbufs
[ 1087.996852] cx8800: Unknown symbol cx88_vdev_init
[ 1087.996893] cx8800: Unknown symbol cx88_core_put
[ 1087.996936] cx8800: Unknown symbol cx88_audio_thread
[ 1087.996965] cx8800: disagrees about version of symbol videobuf_dqbuf
[ 1087.996967] cx8800: Unknown symbol videobuf_dqbuf
[ 1087.997000] cx8800: Unknown symbol cx88_core_irq
[ 1087.997042] cx8800: Unknown symbol cx88_core_get
[ 1087.997074] cx8800: Unknown symbol cx88_get_stereo
[ 1087.997107] cx8800: Unknown symbol cx88_ir_stop
[ 1087.997144] cx8800: Unknown symbol cx88_set_tvnorm
[ 1087.997180] cx8800: Unknown symbol cx88_ir_start
[ 1087.997229] cx8800: disagrees about version of symbol videobuf_stop
[ 1087.997231] cx8800: Unknown symbol videobuf_stop
[ 1087.997293] cx8800: Unknown symbol videobuf_queue_pci_init
[ 1087.997326] cx8800: Unknown symbol cx88_risc_buffer
[ 1087.997348] cx8800: disagrees about version of symbol btcx_riscmem_free
[ 1087.997351] cx8800: Unknown symbol btcx_riscmem_free
[ 1087.997378] cx8800: disagrees about version of symbol videobuf_read_stream
[ 1087.997380] cx8800: Unknown symbol videobuf_read_stream
[ 1087.997420] cx8800: disagrees about version of symbol videobuf_querybuf
[ 1087.997422] cx8800: Unknown symbol videobuf_querybuf
[ 1087.997455] cx8800: Unknown symbol cx88_set_stereo
[ 1087.997478] cx8800: disagrees about version of symbol video_unregister_device
[ 1087.997481] cx8800: Unknown symbol video_unregister_device
[ 1087.997508] cx8800: disagrees about version of symbol videobuf_qbuf
[ 1087.997510] cx8800: Unknown symbol videobuf_qbuf
[ 1087.997548] cx8800: disagrees about version of symbol videobuf_read_one
[ 1087.997550] cx8800: Unknown symbol videobuf_read_one
[ 1087.997590] cx8800: Unknown symbol cx88_sram_channels
[ 1087.997613] cx8800: disagrees about version of symbol video_register_device
[ 1087.997619] cx8800: Unknown symbol video_register_device
[ 1087.997651] cx8800: Unknown symbol cx88_set_tvaudio
[ 1087.997684] cx8800: Unknown symbol cx88_sram_channel_dump
[ 1087.997727] cx8800: Unknown symbol cx88_sram_channel_setup
[ 1087.997759] cx8800: disagrees about version of symbol videobuf_iolock
[ 1087.997761] cx8800: Unknown symbol videobuf_iolock
[ 1087.997793] cx8800: Unknown symbol cx88_free_buffer
[ 1087.997821] cx8800: disagrees about version of symbol videobuf_streamon
[ 1087.997823] cx8800: Unknown symbol videobuf_streamon
[ 1087.997850] cx8800: disagrees about version of symbol videobuf_queue_cancel
[ 1087.997853] cx8800: Unknown symbol videobuf_queue_cancel
[ 1087.997889] cx8800: disagrees about version of symbol video_device_release
[ 1087.997891] cx8800: Unknown symbol video_device_release
[ 1087.997918] cx8800: disagrees about version of symbol videobuf_mmap_mapper
[ 1087.997920] cx8800: Unknown symbol videobuf_mmap_mapper
[ 1087.997950] cx8800: disagrees about version of symbol videobuf_cgmbuf
[ 1087.997953] cx8800: Unknown symbol videobuf_cgmbuf
[ 1087.997986] cx8800: Unknown symbol cx88_newstation
[ 1087.998017] cx8800: disagrees about version of symbol videobuf_to_dma
[ 1087.998019] cx8800: Unknown symbol videobuf_to_dma
[ 1087.998045] cx8800: disagrees about version of symbol videobuf_mmap_free
[ 1087.998048] cx8800: Unknown symbol videobuf_mmap_free
[ 1089.337438] cx88xx: disagrees about version of symbol videobuf_dma_free
[ 1089.337445] cx88xx: Unknown symbol videobuf_dma_free
[ 1089.337489] cx88xx: disagrees about version of symbol videobuf_waiton
[ 1089.337491] cx88xx: Unknown symbol videobuf_waiton
[ 1089.337749] cx88xx: disagrees about version of symbol btcx_riscmem_alloc
[ 1089.337752] cx88xx: Unknown symbol btcx_riscmem_alloc
[ 1089.337797] cx88xx: disagrees about version of symbol btcx_riscmem_free
[ 1089.337799] cx88xx: Unknown symbol btcx_riscmem_free
[ 1089.337821] cx88xx: disagrees about version of symbol videobuf_dma_unmap
[ 1089.337823] cx88xx: Unknown symbol videobuf_dma_unmap
[ 1089.337922] cx88xx: disagrees about version of symbol video_device_alloc
[ 1089.337923] cx88xx: Unknown symbol video_device_alloc
[ 1089.338149] cx88xx: disagrees about version of symbol video_device_release
[ 1089.338152] cx88xx: Unknown symbol video_device_release
[ 1089.338317] cx88xx: disagrees about version of symbol videobuf_to_dma
[ 1089.338319] cx88xx: Unknown symbol videobuf_to_dma
```

I don't know what this all means. Did I not compile video4linux correctly, or something? Anything to get /dev/video0 to appear would be appreciated. (I think that's what I need... right?)

---

### Post by nwr222 on 2008-05-19
Not much help. but I have just tried the same scenario as you have described, and I have identical symptoms.
Are you running 64bit kernel?

---

### Post by nwr222 on 2008-05-21
UPDATE: I have gone back to a Fiesty installation, and got past the problems above.  I now have some contact with the card (Dvico FusionHDTV DVB-T Pro).  I still don't have any TV but the problem has moved on considerably.

---

