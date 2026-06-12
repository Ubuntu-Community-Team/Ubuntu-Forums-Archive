---
title: "v4l-dvb compiling problem"
date: 2008-05-10
forum: Mythbuntu
---

### Post by sith2242 on 2008-05-10
I have i nova-s plus dvb card and I'm trying to compile the v4l-dvb drivers in mythbuntu 8.04.

When I compile the drivers i get lot of warnings :

```
CC [M]  /usr/src/v4l-dvb/v4l/cx18-mailbox.o
  CC [M]  /usr/src/v4l-dvb/v4l/cx18-vbi.o
  CC [M]  /usr/src/v4l-dvb/v4l/cx18-audio.o
  CC [M]  /usr/src/v4l-dvb/v4l/cx18-video.o
  CC [M]  /usr/src/v4l-dvb/v4l/cx18-irq.o
include/asm/io_32.h: In function 'memcpy_fromio':
include/asm/io_32.h:211: warning: passing argument 2 of '__memcpy' discards qualifiers from pointer target type
  CC [M]  /usr/src/v4l-dvb/v4l/cx18-av-core.o
  CC [M]  /usr/src/v4l-dvb/v4l/cx18-av-audio.o
  CC [M]  /usr/src/v4l-dvb/v4l/cx18-av-firmware.o
  CC [M]  /usr/src/v4l-dvb/v4l/cx18-av-vbi.o
  CC [M]  /usr/src/v4l-dvb/v4l/cx18-scb.o
include/asm/io_32.h: In function 'memset_io':
include/asm/io_32.h:205: warning: passing argument 1 of '__constant_c_and_count_memset' discards qualifiers from pointer target type
include/asm/io_32.h:205: warning: passing argument 1 of '__constant_c_memset' discards qualifiers from pointer target type
include/asm/io_32.h:205: warning: passing argument 1 of '__memset_generic' discards qualifiers from pointer target type
include/asm/io_32.h:205: warning: passing argument 1 of '__memset_generic' discards qualifiers from pointer target type
  CC [M]  /usr/src/v4l-dvb/v4l/cx18-dvb.o
  CC [M]  /usr/src/v4l-dvb/v4l/cx23885-cards.o
  CC [M]  /usr/src/v4l-dvb/v4l/cx23885-video.o
  CC [M]  /usr/src/v4l-dvb/v4l/ivtv-ioctl.o
  CC [M]  /usr/src/v4l-dvb/v4l/ivtv-irq.o
include/asm/io_32.h: In function 'memcpy_fromio':
include/asm/io_32.h:211: warning: passing argument 2 of '__memcpy' discards qualifiers from pointer target type
  CC [M]  /usr/src/v4l-dvb/v4l/ivtv-mailbox.o
  CC [M]  /usr/src/v4l-dvb/v4l/ivtv-queue.o
  CC [M]  /usr/src/v4l-dvb/v4l/ivtv-streams.o
  CC [M]  /usr/src/v4l-dvb/v4l/ivtv-udma.o
  CC [M]  /usr/src/v4l-dvb/v4l/zr36060.o
  CC [M]  /usr/src/v4l-dvb/v4l/pms.o
include/asm/io_32.h: In function 'memcpy_fromio':
include/asm/io_32.h:211: warning: passing argument 2 of '__memcpy' discards qualifiers from pointer target type
  CC [M]  /usr/src/v4l-dvb/v4l/stradis.o
  CC [M]  /usr/src/v4l-dvb/v4l/cpia.o
  CC [M]  /usr/src/v4l-dvb/v4l/tcm825x.o
/usr/src/v4l-dvb/v4l/tcm825x.c:892: warning: initialization from incompatible pointer type
  CC [M]  /usr/src/v4l-dvb/v4l/dabusb.o
  CC [M]  /usr/src/v4l-dvb/v4l/konicawc.o
  CC [M]  /usr/src/v4l-dvb/v4l/vicam.o
  CC [M]  /usr/src/v4l-dvb/v4l/quickcam_messenger.o
  LD [M]  /usr/src/v4l-dvb/v4l/ivtv.o
  CC [M]  /usr/src/v4l-dvb/v4l/ivtvfb.o
include/asm/io_32.h: In function 'memset_io':
include/asm/io_32.h:205: warning: passing argument 1 of '__constant_c_and_count_memset' discards qualifiers from pointer target type
include/asm/io_32.h:205: warning: passing argument 1 of '__constant_c_memset' discards qualifiers from pointer target type
include/asm/io_32.h:205: warning: passing argument 1 of '__memset_generic' discards qualifiers from pointer target type
include/asm/io_32.h:205: warning: passing argument 1 of '__memset_generic' discards qualifiers from pointer target type
  LD [M]  /usr/src/v4l-dvb/v4l/cx18.o
  CC [M]  /usr/src/v4l-dvb/v4l/vivi.o
  LD [M]  /usr/src/v4l-dvb/v4l/cx23885.o
  LD [M]  /usr/src/v4l-dvb/v4l/au0828.o
  CC [M]  /usr/src/v4l-dvb/v4l/radio-aztech.o
  CC [M]  /usr/src/v4l-dvb/v4l/radio-rtrack2.o
Building modules, stage 2.
  MODPOST 232 modules
  CC      /usr/src/v4l-dvb/v4l/adv7170.mod.o
  LD [M]  /usr/src/v4l-dvb/v4l/adv7170.ko
  CC      /usr/src/v4l-dvb/v4l/adv7175.mod.o
  LD [M]  /usr/src/v4l-dvb/v4l/zc0301.ko
  CC      /usr/src/v4l-dvb/v4l/zl10353.mod.o
  LD [M]  /usr/src/v4l-dvb/v4l/zl10353.ko
  CC      /usr/src/v4l-dvb/v4l/zr36016.mod.o
  LD [M]  /usr/src/v4l-dvb/v4l/zr36016.ko
  CC      /usr/src/v4l-dvb/v4l/zr36050.mod.o
  LD [M]  /usr/src/v4l-dvb/v4l/zr36050.ko
  CC      /usr/src/v4l-dvb/v4l/zr36060.mod.o
  LD [M]  /usr/src/v4l-dvb/v4l/zr36060.ko
  CC      /usr/src/v4l-dvb/v4l/zr36067.mod.o
  LD [M]  /usr/src/v4l-dvb/v4l/zr36067.ko
  CC      /usr/src/v4l-dvb/v4l/zr364xx.mod.o
  LD [M]  /usr/src/v4l-dvb/v4l/zr364xx.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
./scripts/rmmod.pl check
found 232 modules
make[1]: Leaving directory `/usr/src/v4l-dvb/v4l'
```

an if I do dmesg if show this :

```
  31.945959] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   31.967917] Linux agpgart interface v0.102
[   32.240953] intel_rng: FWH not detected
[   32.980334] input: Power Button (FF) as /devices/virtual/input/input3
[   33.015536] ACPI: Power Button (FF) [PWRF]
[   33.015656] input: Power Button (CM) as /devices/virtual/input/input4
[   33.047449] ACPI: Power Button (CM) [PWRB]
[   33.341199] Linux video capture interface: v2.00
[   33.447721] cx88xx: disagrees about version of symbol videobuf_waiton
[   33.447727] cx88xx: Unknown symbol videobuf_waiton
[   33.448495] cx88xx: disagrees about version of symbol videobuf_dma_unmap
[   33.448499] cx88xx: Unknown symbol videobuf_dma_unmap
[   33.448752] cx88xx: disagrees about version of symbol video_device_alloc
[   33.448755] cx88xx: Unknown symbol video_device_alloc
[   33.449321] cx88xx: disagrees about version of symbol video_device_release
[   33.449324] cx88xx: Unknown symbol video_device_release
[   33.449743] cx88xx: disagrees about version of symbol videobuf_to_dma
[   33.449747] cx88xx: Unknown symbol videobuf_to_dma
[   33.462418] cx8800: disagrees about version of symbol videobuf_streamoff
[   33.462424] cx8800: Unknown symbol videobuf_streamoff
[   33.462562] cx8800: Unknown symbol cx88_reset
[   33.462622] cx8800: disagrees about version of symbol videobuf_poll_stream
[   33.462625] cx8800: Unknown symbol videobuf_poll_stream
[   33.462745] cx8800: Unknown symbol cx88_call_i2c_clients
[   33.462814] cx8800: Unknown symbol cx88_wakeup
[   33.462910] cx8800: Unknown symbol cx88_risc_stopper
[   33.463115] cx8800: Unknown symbol cx88_print_irqbits
[   33.463248] cx8800: Unknown symbol cx88_set_scale
[   33.463375] cx8800: Unknown symbol cx88_shutdown
[   33.463433] cx8800: disagrees about version of symbol videobuf_reqbufs
[   33.463435] cx8800: Unknown symbol videobuf_reqbufs
[   33.463499] cx8800: Unknown symbol cx88_vdev_init
[   33.463607] cx8800: Unknown symbol cx88_core_put
[   33.463708] cx8800: Unknown symbol cx88_audio_thread
[   33.463768] cx8800: disagrees about version of symbol videobuf_dqbuf
[   33.463772] cx8800: Unknown symbol videobuf_dqbuf
[   33.463840] cx8800: Unknown symbol cx88_core_irq
[   33.463938] cx8800: Unknown symbol cx88_core_get
[   33.464006] cx8800: Unknown symbol cx88_get_stereo
[   33.464075] cx8800: Unknown symbol cx88_ir_stop
[   33.464155] cx8800: Unknown symbol cx88_set_tvnorm
[   33.464234] cx8800: Unknown symbol cx88_ir_start
[   33.464343] cx8800: disagrees about version of symbol videobuf_stop
[   33.464346] cx8800: Unknown symbol videobuf_stop
[   33.464468] cx8800: Unknown symbol videobuf_queue_pci_init
[   33.464536] cx8800: Unknown symbol cx88_risc_buffer
[   33.464649] cx8800: disagrees about version of symbol videobuf_read_stream
[   33.464652] cx8800: Unknown symbol videobuf_read_stream
[   33.464749] cx8800: disagrees about version of symbol videobuf_querybuf
[   33.464752] cx8800: Unknown symbol videobuf_querybuf
[   33.464820] cx8800: Unknown symbol cx88_set_stereo
[   33.464874] cx8800: disagrees about version of symbol video_unregister_device
[   33.464877] cx8800: Unknown symbol video_unregister_device
[   33.464936] cx8800: disagrees about version of symbol videobuf_qbuf
[   33.464939] cx8800: Unknown symbol videobuf_qbuf
[   33.465028] cx8800: disagrees about version of symbol videobuf_read_one
[   33.465031] cx8800: Unknown symbol videobuf_read_one
[   33.465132] cx8800: Unknown symbol cx88_sram_channels
[   33.465186] cx8800: disagrees about version of symbol video_register_device
[   33.465189] cx8800: Unknown symbol video_register_device
[   33.465257] cx8800: Unknown symbol cx88_set_tvaudio
[   33.465326] cx8800: Unknown symbol cx88_sram_channel_dump
[   33.465430] cx8800: Unknown symbol cx88_sram_channel_setup
[   33.465500] cx8800: disagrees about version of symbol videobuf_iolock
[   33.465503] cx8800: Unknown symbol videobuf_iolock
[   33.465571] cx8800: Unknown symbol cx88_free_buffer
[   33.465629] cx8800: disagrees about version of symbol videobuf_streamon
[   33.465632] cx8800: Unknown symbol videobuf_streamon
[   33.465694] cx8800: disagrees about version of symbol videobuf_queue_cancel
[   33.465697] cx8800: Unknown symbol videobuf_queue_cancel
[   33.465787] cx8800: disagrees about version of symbol video_device_release
[   33.465790] cx8800: Unknown symbol video_device_release
[   33.465845] cx8800: disagrees about version of symbol videobuf_mmap_mapper
[   33.465849] cx8800: Unknown symbol videobuf_mmap_mapper
[   33.465916] cx8800: disagrees about version of symbol videobuf_cgmbuf
[   33.465919] cx8800: Unknown symbol videobuf_cgmbuf
[   33.465992] cx8800: Unknown symbol cx88_newstation
[   33.466081] cx8800: disagrees about version of symbol videobuf_to_dma
[   33.466084] cx8800: Unknown symbol videobuf_to_dma
[   33.466140] cx8800: disagrees about version of symbol videobuf_mmap_free
[   33.466143] cx8800: Unknown symbol videobuf_mmap_free
[   33.467178] cx88xx: disagrees about version of symbol videobuf_waiton
[   33.467182] cx88xx: Unknown symbol videobuf_waiton
[   33.467949] cx88xx: disagrees about version of symbol videobuf_dma_unmap
[   33.467953] cx88xx: Unknown symbol videobuf_dma_unmap
[   33.468201] cx88xx: disagrees about version of symbol video_device_alloc
[   33.468205] cx88xx: Unknown symbol video_device_alloc
[   33.468757] cx88xx: disagrees about version of symbol video_device_release
[   33.468761] cx88xx: Unknown symbol video_device_release
[   33.469186] cx88xx: disagrees about version of symbol videobuf_to_dma
[   33.469190] cx88xx: Unknown symbol videobuf_to_dma
[   33.496340] cx88xx: disagrees about version of symbol videobuf_waiton
[   33.496345] cx88xx: Unknown symbol videobuf_waiton
[   33.497123] cx88xx: disagrees about version of symbol videobuf_dma_unmap
[   33.497127] cx88xx: Unknown symbol videobuf_dma_unmap
[   33.497382] cx88xx: disagrees about version of symbol video_device_alloc
[   33.497385] cx88xx: Unknown symbol video_device_alloc
[   33.497939] cx88xx: disagrees about version of symbol video_device_release
[   33.497942] cx88xx: Unknown symbol video_device_release
[   33.498360] cx88xx: disagrees about version of symbol videobuf_to_dma
[   33.498363] cx88xx: Unknown symbol videobuf_to_dma
[   33.509181] cx8802: Unknown symbol cx88_reset
[   33.509252] cx8802: Unknown symbol cx88_wakeup
[   33.509347] cx8802: Unknown symbol cx88_risc_stopper
[   33.509440] cx8802: Unknown symbol cx88_print_irqbits
[   33.509540] cx8802: Unknown symbol cx88_shutdown
[   33.509618] cx8802: Unknown symbol cx88_core_put
[   33.509714] cx8802: Unknown symbol cx88_core_irq
[   33.509809] cx8802: Unknown symbol cx88_core_get
[   33.510026] cx8802: Unknown symbol cx88_sram_channels
[   33.510095] cx8802: Unknown symbol cx88_sram_channel_dump
[   33.510175] cx8802: Unknown symbol cx88_sram_channel_setup
[   33.510246] cx8802: disagrees about version of symbol videobuf_iolock
[   33.510249] cx8802: Unknown symbol videobuf_iolock
[   33.510318] cx8802: Unknown symbol cx88_free_buffer
[   33.510484] cx8802: Unknown symbol cx88_risc_databuffer
[   33.510541] cx8802: disagrees about version of symbol videobuf_to_dma
[   33.510544] cx8802: Unknown symbol videobuf_to_dma
[   33.758577] cx88_alsa: Unknown symbol cx88_print_irqbits
[   33.758874] cx88_alsa: Unknown symbol cx88_core_put
[   33.759005] cx88_alsa: Unknown symbol videobuf_pci_alloc
[   33.759078] cx88_alsa: Unknown symbol cx88_core_irq
[   33.759175] cx88_alsa: Unknown symbol cx88_core_get
[   33.759783] cx88_alsa: Unknown symbol cx88_sram_channels
[   33.759854] cx88_alsa: Unknown symbol cx88_sram_channel_dump
[   33.759952] cx88_alsa: Unknown symbol cx88_sram_channel_setup
[   33.760123] cx88_alsa: Unknown symbol videobuf_pci_dma_unmap
[   33.760265] cx88_alsa: Unknown symbol videobuf_pci_dma_map
[   33.760360] cx88_alsa: Unknown symbol cx88_risc_databuffer
[   33.760419] cx88_alsa: disagrees about version of symbol videobuf_to_dma
[   33.760422] cx88_alsa: Unknown symbol videobuf_to_dma
[   33.895222] nvidia: module license 'NVIDIA' taints kernel.
[   34.255802] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   34.397609] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.397626] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   34.397918] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   34.698393] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.698423] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   36.009210] lp0: using parport0 (interrupt-driven).
[   36.307220] Adding 1494004k swap on /dev/sda5.  Priority:-1 exten
```

Does anyone had this problem and Any Idea how can I fix this?

Thank you 
sith2242

---

### Post by ian dobson on 2008-05-10
Hi,

Have a look here:[http://www.mythtv.org/pipermail/mythtv-users/2008-April/219685.html](http://www.mythtv.org/pipermail/mythtv-users/2008-April/219685.html)

It looks as if you have a "mix and unmatch" version of dvb_core and the cx modules.

Regards
Ian Dobson

---

### Post by sith2242 on 2008-05-15
Thanks ian dobson, that was exactly what i needed, I manage to find the conflicting modules and remove them. I recompile the v4l-dvb drives and everything is working great. Thank's for youre help

---

