---
title: "Compro VideoMate C100 doesn't work"
date: 2011-02-17
forum: Multimedia Software
---

### Post by ceperman on 2011-02-17
I'm trying to get a Compro Videomate C100 video capture card working with Ubuntu 10.10. Currently it fails to initialize.

DMESG says this:

[   13.379260] saa7134 0000:04:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   13.379266] saa7134[0]: found at 0000:04:00.0, rev: 1, irq: 20, latency: 64, mmio: 0xfebffc00
[   13.379272] saa7134[0]: subsystem: 185b:c900, board: Compro Videomate DVB-T300 [card=70,autodetected]
[   13.379289] saa7134[0]: board init: gpio is 880000
[   13.380123] type=1400 audit(1297958432.397:9): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=665 comm="apparmor_parser"
[   13.384199] IR RC6 protocol handler initialized
[   13.388013] leds_ss4200: no LED devices found
[   13.392221] IR JVC protocol handler initialized
[   13.394791] IR Sony protocol handler initialized
[   13.401017] lirc_dev: IR Remote Control driver registered, major 251 
[   13.402489] IR LIRC bridge handler initialized
[   13.405878] [fglrx] Maximum main memory to use for locked dma buffers: 3373 MBytes.
[   13.406072] [fglrx]   vendor: 1002 device: 954f count: 1
[   13.406526] [fglrx] ioport: bar 4, base 0xd000, size: 0x100
[   13.406544] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.406548] pci 0000:01:00.0: setting latency timer to 64
[   13.406833] [fglrx] Kernel PAT support is enabled
[   13.406854] [fglrx] module loaded - fglrx 8.78.30 [Sep 20 2010] with 1 minors
[   13.409576] Registered IR keymap rc-videomate-tv-pvr
[   13.409674] input: saa7134 IR (Compro Videomate DV as /devices/pci0000:00/0000:00:1e.0/0000:04:00.0/rc/rc0/input3
[   13.409736] rc0: saa7134 IR (Compro Videomate DV as /devices/pci0000:00/0000:00:1e.0/0000:04:00.0/rc/rc0
[   13.443765] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.443840]   alloc irq_desc for 44 on node -1
[   13.443842]   alloc kstat_irqs on node -1
[   13.443853] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   13.443874] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.457663] lp0: using parport0 (interrupt-driven).
[   13.493224] hda_codec: ALC887: BIOS auto-probing.
[   13.505191]   alloc irq_desc for 17 on node -1
[   13.505195]   alloc kstat_irqs on node -1
[   13.505210] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   13.505276]   alloc irq_desc for 45 on node -1
[   13.505277]   alloc kstat_irqs on node -1
[   13.505285] HDA Intel 0000:01:00.1: irq 45 for MSI/MSI-X
[   13.505314] HDA Intel 0000:01:00.1: setting latency timer to 64
[   13.558199] psmouse serio1: ID: 10 00 64
[   13.561506] saa7134[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   13.561519] saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   13.561530] saa7134[0]: i2c eeprom 20: 01 40 01 02 02 03 01 03 08 ff 00 89 ff ff ff ff
[   13.561541] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.561552] saa7134[0]: i2c eeprom 40: ff da 00 ff 86 ff ff ff ff ff ff ff 5a ff 03 17
[   13.561563] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[   13.561573] saa7134[0]: i2c eeprom 60: 34 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.561584] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.561595] saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.561606] saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.561616] saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.561627] saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.561638] saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.561649] saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.561659] saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.561670] saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.565549] tuner 0-0061: chip found @ 0xc2 (saa7134[0])
[   13.567955] tuner-simple 0-0061: unable to probe Philips TD1316 Hybrid Tuner, proceeding anyway.
[   13.567957] tuner-simple 0-0061: creating new instance
[   13.567959] tuner-simple 0-0061: type set to 67 (Philips TD1316 Hybrid Tuner)
[   13.568138] tuner-simple 0-0061: i2c i/o error: rc == -5 (should be 4)
[   13.568317] tuner-simple 0-0061: i2c i/o error: rc == -5 (should be 4)
[   13.568494] tuner-simple 0-0061: i2c i/o error: rc == -5 (should be 4)
[   13.568628] saa7134[0]: registered device video0 [v4l2]
[   13.568657] saa7134[0]: registered device vbi0
[   13.573639] saa7134 ALSA driver for DMA sound loaded
[   13.573667] saa7134[0]/alsa: saa7134[0] at 0xfebffc00 irq 20 registered as card -2
[   13.575852] tuner-simple 0-0061: i2c i/o error: rc == -5 (should be 4)
[   13.577121] tuner-simple 0-0061: i2c i/o error: rc == -5 (should be 4)
[   13.581444] dvb_init() allocating 1 frontend
[   13.583435] tda10046: chip is not answering. Giving up.
[   13.583515] saa7134[0]/dvb: frontend initialization failed

The system autodetects it as a Compro Videomate DVB-T300 (card=70) - this is a TV card but the C100 has no tuner. I've added tuner=4 (no tuner) to the modprobe saa7134 options, but this just has the effect of removing the error messages associated with the tuner. Ultimately, initialization always fails with the message "tda10046: chip is not answering. Giving up."

I've tried various other Compro card values (from the saa7134 card list) - 71 and 103 give the same init failed. With types 19, 40 41, 49 and 62 the init succeeds. I've used GUVCVideo as my test app, and it can see the card which it initializes OK but captures nothing. I've randomly tried non-Compro values without any success, except with card=18 (BMK MPEX No Tuner) I capture static - not sure what this indicates.

The unsuccessful attempts to use the card when it does initialize OK appear to produce these entries in syslog:

Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c: snd_pcm_avail_delay() returned strange values: delay 0 is less than avail 8.
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c: snd_pcm_dump():
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c: Soft volume PCM
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c: Control: PCM Playback Volume
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c: min_dB: -51
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c: max_dB: 0
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c: resolution: 256
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c: Its setup is:
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   stream       : CAPTURE
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   access       : MMAP_INTERLEAVED
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   format       : S16_LE
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   subformat    : STD
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   channels     : 2
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   rate         : 44100
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   exact rate   : 44100 (44100/1)
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   msbits       : 16
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   buffer_size  : 88192
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   period_size  : 44096
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   period_time  : 999909
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   tstamp_mode  : ENABLE
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   period_step  : 1
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   avail_min    : 87310
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   period_event : 0
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   start_threshold  : -1
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   stop_threshold   : 1444937728
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   silence_threshold: 0
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   silence_size : 0
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   boundary     : 1444937728
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c: Its setup is:
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   stream       : CAPTURE
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   access       : MMAP_INTERLEAVED
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   format       : S16_LE
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   subformat    : STD
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   channels     : 2
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   rate         : 44100
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   exact rate   : 44100 (44100/1)
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   msbits       : 16
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   buffer_size  : 88192
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   period_size  : 44096
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   period_time  : 999909
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   tstamp_mode  : ENABLE
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   period_step  : 1
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   avail_min    : 87310
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   period_event : 0
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   start_threshold  : -1
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   stop_threshold   : 1444937728
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   silence_threshold: 0
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   silence_size : 0
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   boundary     : 1444937728
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   appl_ptr     : 87256
Feb 17 17:08:34 home pulseaudio[1487]: alsa-util.c:   hw_ptr       : 87256

Maybe there are other parms for saa7134 that I should be using.

I'd appreciate any advice to help here.

---

