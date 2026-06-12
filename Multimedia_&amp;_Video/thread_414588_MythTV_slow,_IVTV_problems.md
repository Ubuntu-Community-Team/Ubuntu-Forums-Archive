---
title: "MythTV slow, IVTV problems?"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by tuco penguin on 2007-04-20
I recently got mythtv backend installed on an older computer (Dell Optiplex 1.8 GHz P4) running Dapper as a LAMP server.  While I've managed to get things at least functional, things are very slow.  Right now, my office PC (similar vintage AMD, running Edgy) is the frontend machine, but once I get everything tuned up I'll be building a small, quiet frontend for the living room.

I suspect a number of different problems I may have to slog through to get the setup running smoothly.  That's OK... it's a good exercise before I go live in front of the whole family down in the living room.  It is just painfully slow right now and I wonder if anyone can help troubleshoot the first obvious problem, which appears when I type the dmesg command on the backend machine.  I'm cutting out just the IVTV section, which ends with a whole bunch of repeated errors regarding buffer overflow (but may also show some other hints, like disabled IRQs.):
```
[42949385.810000] ivtv:  ==================== START INIT IVTV ====================
[42949385.810000] ivtv:  version 0.4.10 (tagged release) loading
[42949385.810000] ivtv:  Linux version: 2.6.15-26-server SMP 686 gcc-4.0
[42949385.810000] ivtv:  In case of problems please include the debug info between
[42949385.810000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[42949385.810000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[42949385.810000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[42949385.850000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[42949385.960000] tveeprom: Second (radio) tuner idx 101
[42949385.960000] tveeprom: ivtv version
[42949385.960000] tveeprom: Hauppauge: model = 23552, rev = E787, serial# = 9925595
[42949385.960000] tveeprom: tuner = Samsung TCPN 2221P30A (idx = 87, type = 68)
[42949385.960000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[42949385.960000] tveeprom: audio processor = CX25843 (type = 25)
[42949385.960000] tveeprom: decoder processor = CX25843 (type = 1e)
[42949385.960000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[42949385.960000] ivtv0: This is the first unit of a PVR500
[42949385.970000] tuner (ivtv): chip found at addr 0xc0 i2c-bus ivtv i2c driver #0
[42949385.970000] TEA5767 detected.
[42949385.970000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=60]
[42949385.970000] tuner: type set to 62 (Philips TEA5767HN FM Radio) by autodetect
[42949385.970000] type set to 62 (Philips TEA5767HN FM Radio)
[42949385.970000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[42949385.970000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[42949386.220000] cx25840 0-0044: ivtv driver
[42949386.220000] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[42949386.270000] intel8x0_measure_ac97_clock: measured 58782 usecs
[42949386.270000] intel8x0: clocking to 41165
[42949391.070000] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[42949391.170000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[42949391.210000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[42949391.220000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[42949391.280000] ivtv0: Detected a TEA5767 radio tuner. Enabling radio support.
[42949391.520000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[42949391.970000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[42949392.190000] ivtv0: Encoder revision: 0x02060039
[42949392.190000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[42949392.190000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[42949392.190000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[42949392.190000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[42949392.190000] ivtv0: Create encoder radio stream
[42949392.190000] tuner: type set to 68 (Samsung TCPN 2221P30A) by ivtv i2c driver #0
[42949392.320000] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[42949392.320000] ivtv:  ======================  NEXT CARD  ======================
[42949392.320000] ivtv1: Autodetected WinTV PVR 150 card (cx23416 based)
[42949392.380000] tveeprom: Second (radio) tuner idx 101
[42949392.380000] tveeprom: ivtv version
[42949392.380000] tveeprom: Hauppauge: model = 23552, rev = E787, serial# = 9925595
[42949392.380000] tveeprom: tuner = Samsung TCPN 2221P30A (idx = 87, type = 68)
[42949392.380000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[42949392.380000] tveeprom: audio processor = CX25843 (type = 25)
[42949392.380000] tveeprom: decoder processor = CX25843 (type = 1e)
[42949392.380000] ivtv1: i2c attach to card #1 ok [client=tveeprom, addr=50]
[42949392.400000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #1
[42949392.400000] ivtv1: i2c attach to card #1 ok [client=(tuner unset), addr=61]
[42949392.630000] cx25840 1-0044: ivtv driver
[42949392.630000] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[42949397.460000] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[42949397.560000] ivtv1: i2c attach to card #1 ok [client=cx25840, addr=44]
[42949397.560000] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #1)
[42949397.570000] ivtv1: i2c attach to card #1 ok [client=wm8775, addr=1b]
[42949397.630000] ivtv1: This is the first unit of a PVR500
[42949397.670000] NET: Registered protocol family 17
[42949398.360000] ivtv1: loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[42949398.580000] ivtv1: Encoder revision: 0x02060039
[42949398.580000] ivtv1: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[42949398.580000] ivtv1: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[42949398.580000] ivtv1: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[42949398.580000] ivtv1: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[42949398.580000] ivtv1: Create encoder radio stream
[42949398.580000] tuner: type set to 68 (Samsung TCPN 2221P30A) by ivtv i2c driver #1
[42949398.710000] ivtv1: Initialized WinTV PVR 500 (unit #1), card #1
[42949398.710000] ivtv:  ====================  END INIT IVTV  ====================
[42949399.080000] lp0: using parport0 (interrupt-driven).
[42949399.260000] Adding 1638588k swap on /dev/hda8.  Priority:-1 extents:1 across:1638588k
[42949399.340000] EXT3 FS on hda6, internal journal
[42949399.600000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[42949399.600000] md: bitmap version 4.39
[42949400.110000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[42949400.720000] cdrom: open failed.
[42949401.530000] kjournald starting.  Commit interval 5 seconds
[42949401.540000] EXT3 FS on hda5, internal journal
[42949401.540000] EXT3-fs: mounted filesystem with ordered data mode.
[42949401.580000] kjournald starting.  Commit interval 5 seconds
[42949401.590000] EXT3 FS on hda7, internal journal
[42949401.590000] EXT3-fs: mounted filesystem with ordered data mode.
[42949401.670000] JFS: nTxBlock = 4023, nTxLock = 32190
[42949402.140000] smbfs: Unrecognized mount option umask
[42949402.550000] NET: Registered protocol family 10
[42949402.560000] lo: Disabled Privacy Extensions
[42949402.560000] IPv6 over IPv4 tunneling driver
[42949404.400000] ppdev: user-space parallel port driver
[42949413.390000] eth0: no IPv6 routers present
[42949861.200000] irq 177: nobody cared (try booting with the "irqpoll" option)
[42949861.200000]  [<c014de9a>] __report_bad_irq+0x2a/0xa0
[42949861.200000]  [<c014d64d>] handle_IRQ_event+0x3d/0x70
[42949861.200000]  [<c014dfb7>] note_interrupt+0x87/0xf0
[42949861.200000]  [<c014d76f>] __do_IRQ+0xef/0x100
[42949861.200000]  [<c0105ad9>] do_IRQ+0x19/0x30
[42949861.200000]  [<c0103daa>] common_interrupt+0x1a/0x20
[42949861.200000]  [<c0101030>] default_idle+0x0/0x60
[42949861.200000]  [<c010105c>] default_idle+0x2c/0x60
[42949861.200000]  [<c010111f>] cpu_idle+0x6f/0xc0
[42949861.200000]  [<c03ada35>] start_kernel+0x195/0x200
[42949861.200000]  [<c03ad3c0>] unknown_bootoption+0x0/0x1f0
[42949861.200000] handlers:
[42949861.200000] [<e08d0180>] (usb_hcd_irq+0x0/0x70 [usbcore])
[42949861.200000] Disabling IRQ #177
[42950255.770000] irq 169: nobody cared (try booting with the "irqpoll" option)
[42950255.770000]  [<c014de9a>] __report_bad_irq+0x2a/0xa0
[42950255.770000]  [<c014d64d>] handle_IRQ_event+0x3d/0x70
[42950255.770000]  [<c014dfb7>] note_interrupt+0x87/0xf0
[42950255.770000]  [<c014d76f>] __do_IRQ+0xef/0x100
[42950255.770000]  [<c0105ad9>] do_IRQ+0x19/0x30
[42950255.770000]  [<c0103daa>] common_interrupt+0x1a/0x20
[42950255.770000]  [<e0a63000>] ivtv_getscl+0x10/0x20 [ivtv]
[42950255.770000]  [<e0a63049>] ivtv_scldelay+0x19/0x30 [ivtv]
[42950255.770000]  [<e0a630cb>] ivtv_waitsda+0x1b/0x50 [ivtv]
[42950255.770000]  [<e0a63152>] ivtv_ack+0x52/0x150 [ivtv]
[42950255.770000]  [<e0a63906>] ivtv_write+0xd6/0x150 [ivtv]
[42950255.770000]  [<e0a63bce>] ivtv_xfer+0xee/0x180 [ivtv]
[42950255.770000]  [<c0106468>] do_sys_vm86+0xc8/0x160
[42950255.770000]  [<e09b2e08>] i2c_transfer+0x38/0x50 [i2c_core]
[42950255.770000]  [<e09b2e67>] i2c_master_send+0x47/0x60 [i2c_core]
[42950255.770000]  [<e09f60d4>] cx25840_read+0x34/0x70 [cx25840]
[42950255.770000]  [<e09f6d79>] cx25840_get_v4lstd+0x19/0xd0 [cx25840]
[42950255.770000]  [<e09f9cc1>] cx25840_vbi+0x21/0x5b0 [cx25840]
[42950255.770000]  [<c014d739>] __do_IRQ+0xb9/0x100
[42950255.770000]  [<c0106468>] do_sys_vm86+0xc8/0x160
[42950255.770000]  [<e0a63eae>] ivtv_call_i2c_client+0x15e/0x1d0 [ivtv]
[42950255.770000]  [<c0106468>] do_sys_vm86+0xc8/0x160
[42950255.770000]  [<c0106468>] do_sys_vm86+0xc8/0x160
[42950255.770000]  [<e0a63fa8>] ivtv_cx25840+0x28/0x30 [ivtv]
[42950255.770000]  [<c0106468>] do_sys_vm86+0xc8/0x160
[42950255.770000]  [<e0a6e7da>] compress_sliced_buf+0xda/0x150 [ivtv]
[42950255.770000]  [<c0106468>] do_sys_vm86+0xc8/0x160
[42950255.770000]  [<e0a6e9cc>] ivtv_process_vbi_data+0x17c/0x220 [ivtv]
[42950255.770000]  [<e0a6b364>] ivtv_FROM_DMA_done+0x1d4/0x280 [ivtv]
[42950255.770000]  [<e0a6c6c9>] ivtv_sched_VBI+0x469/0x7dc [ivtv]
[42950255.770000]  [<c011f850>] default_wake_function+0x0/0x20
[42950255.770000]  [<e0a6f8b1>] enc_vbi_work_handler+0x31/0x40 [ivtv]
[42950255.770000]  [<e0a7120f>] ivtv_enc_vbi_thread+0x13f/0x200 [ivtv]
[42950255.770000]  [<c01033d2>] work_resched+0x5/0x16
[42950255.770000]  [<c013c130>] autoremove_wake_function+0x0/0x60
[42950255.770000]  [<e0a710d0>] ivtv_enc_vbi_thread+0x0/0x200 [ivtv]
[42950255.770000]  [<c0101505>] kernel_thread_helper+0x5/0x10
[42950255.770000] handlers:
[42950255.770000] [<e09b9920>] (snd_intel8x0_interrupt+0x0/0x290 [snd_intel8x0])
[42950255.770000] [<e0a6a9f0>] (ivtv_irq_handler+0x0/0x7a0 [ivtv])
[42950255.770000] Disabling IRQ #169
[42950262.790000] ivtv0: All encoder MPEG stream buffers are full. Dropping data.
[42950262.790000] ivtv0: Cause: the application is not reading fast enough.
[42950264.900000] ivtv0: All encoder MPEG stream buffers are full. Dropping data.
[42950264.900000] ivtv0: Cause: the application is not reading fast enough.
[42950265.670000] ivtv0: All encoder MPEG stream buffers are full. Dropping data.
[42950265.670000] ivtv0: Cause: the application is not reading fast enough.
[42950265.880000] ivtv0: All encoder MPEG stream buffers are full. Dropping data.
[42950265.880000] ivtv0: Cause: the application is not reading fast enough.

(and a whole bunch moreof the above two lines)
```

Thoughts?  Are the disabled IRQs a problem, and how can I prevent the buffer overflows?

---

### Post by bnuytten on 2007-04-20
> [42950255.770000] irq 169: nobody cared (try booting with the "irqpoll" option)
This is the first option. Have you tried it? See /boot/grub/menu.lst or edit it at boot time by pressing "e".

Second option: try accessing your capture card without using mythtv. Check with dstat or top the CPU usage and I/O wait.
```
cat /dev/vide0 > test.capture
```

I had problems with mythtv being slow but this had nothing todo with the ivtv driver. In the end all I had to do was tweak the Xorg configuration to enable graphics hardware acceleration :-) Gone was the long and high iowait stuff...

---

