---
title: "TV Tuner no sound"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by c3rb3rus on 2007-05-10
I am having problems getting sounds from my tv tuner (KWorld ATSC110).  I followed the directions here: [http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110](http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110) but i still cant seem to get audio via the PCI bus.

the saa7134 device shows up in alsamixer as card 1

here is the output from dmesg from the point it loads the tv tuner on:

```
[   30.366465] saa7130/34: v4l2 driver version 0.2.14 loaded
[   30.367142] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   30.367146] ACPI: PCI Interrupt 0000:04:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   30.367154] saa7133[0]: found at 0000:04:08.0, rev: 240, irq: 16, latency: 32, mmio: 0xfdbfe000
[   30.367161] saa7133[0]: subsystem: 17de:7350, board: Kworld ATSC110 [card=90,autodetected]
[   30.367171] saa7133[0]: board init: gpio is 100
[   30.517048] saa7133[0]: i2c eeprom 00: de 17 50 73 ff ff ff ff ff ff ff ff ff ff ff ff
[   30.517057] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.517065] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.517072] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.517079] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.517086] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.517093] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.517100] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.612937] tuner 2-0061: chip found @ 0xc2 (saa7133[0])
[   30.612975] tuner 2-0061: type set to 68 (Philips TUV1236D ATSC/NTSC dual in)
[   30.612979] tuner 2-0061: type set to 68 (Philips TUV1236D ATSC/NTSC dual in)
[   30.615076] saa7133[0]: registered device video0 [v4l2]
[   30.615100] saa7133[0]: registered device vbi0
[   30.616061] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   30.616065] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [AAZA] -> GSI 22 (level, low) -> IRQ 22
[   30.616088] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   30.627475] saa7134 ALSA driver for DMA sound loaded
[   30.627505] saa7133[0]/alsa: saa7133[0] at 0xfdbfe000 irq 16 registered as card -2
[   30.941215] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   31.076028] fuse init (API version 7.8)
[   31.100176] lp0: using parport0 (interrupt-driven).
[   31.244381] nxt200x: NXT2004 Detected
[   31.244418] DVB: registering new adapter (saa7133[0]).
[   31.244422] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   31.285254] Adding 1951888k swap on /dev/disk/by-uuid/889ee95d-ba4e-483c-8256-46ba8f18f2c9.  Priority:-1 extents:1 across:1951888k
[   31.365182] EXT3 FS on sda1, internal journal
[   31.569102] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[   31.569349] SGI XFS Quota Management subsystem
[   31.604879] XFS mounting filesystem sda3
[   31.685018] Ending clean XFS mount for filesystem: sda3
[   32.816867] NET: Registered protocol family 10
[   32.816972] lo: Disabled Privacy Extensions
[   37.956402] No dock devices found.
[   38.029422] Using specific hotkey driver
[   38.067369] ibm_acpi: ec object not found
[   38.166381] input: Power Button (FF) as /class/input/input4
[   38.170379] ACPI: Power Button (FF) [PWRF]
[   38.197580] input: Power Button (CM) as /class/input/input5
[   38.197624] ACPI: Power Button (CM) [PWRB]
[   38.238573] pcc_acpi: loading...
[   38.408795] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ processors (version 2.00.00)
[   38.408819] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0xa
[   38.408824] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xb
[   38.408826] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   45.041313] ppdev: user-space parallel port driver
[   49.155986] Bluetooth: Core ver 2.11
[   49.156043] NET: Registered protocol family 31
[   49.156046] Bluetooth: HCI device and connection manager initialized
[   49.156050] Bluetooth: HCI socket layer initialized
[   49.196709] Bluetooth: L2CAP ver 2.8
[   49.196714] Bluetooth: L2CAP socket layer initialized
[   49.223542] Bluetooth: RFCOMM socket layer initialized
[   49.223561] Bluetooth: RFCOMM TTY layer initialized
[   49.223563] Bluetooth: RFCOMM ver 1.8
[   50.006584] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   50.040297] nxt2004: Waiting for firmware upload(2)...
[   51.579702] nxt2004: Firmware upload complete
[   54.250429] eth0: no IPv6 routers present

```

Here is my 'lsmod | grep alsa' output:
```
saa7134_alsa           17184  0
snd_pcm                92808  4 saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    68904  11 saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
saa7134               139880  2 saa7134_dvb,saa7134_alsa
video_buf              29700  4 saa7134_dvb,video_buf_dvb,saa7134_alsa,saa7134

```

Here is my /etc/modules file:
```
fuse
lp
rtc
sbp2
saa7134
saa7134-dvb
saa7134-alsa index=1
```


I am lost :(

let me know if more information is needed.  Thanks for the help!

---

