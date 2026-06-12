---
title: "no live TV after cold start but after warmstart after used with Vista"
date: 2010-01-21
forum: Multimedia Software
---

### Post by Rschnauzer on 2010-01-21
Hallo,

may anybody help me to initalize the TV adapter card [Creatix CTX948]("http://www.creatix.de/produkte/multimedia/datenblatt/CTX948%20V1%20Specification.pdf")
Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
After a cold start I get no DVB-S TV with Klear (error message) and VLC (no message).

If I use the DVB-S card with Vista and warm-start Ubuntu both applications work with video and audio.

I hope i copied all needed messages after cold start
```
Jan 21 22:10:48 BYIZB3 kernel: [   14.056755] saa7130/34: v4l2 driver version 0.2.15 loaded
Jan 21 22:10:48 BYIZB3 kernel: [   14.056798] saa7134 0000:02:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 21 22:10:48 BYIZB3 kernel: [   14.056803] saa7133[0]: found at 0000:02:01.0, rev: 209, irq: 17, latency: 84, mmio: 0xfddff000
Jan 21 22:10:48 BYIZB3 kernel: [   14.056809] saa7133[0]: subsystem: 16be:000d, board: Medion Md8800 Quadro [card=96,autodetected]
Jan 21 22:10:48 BYIZB3 kernel: [   14.056820] saa7133[0]: board init: gpio is 0
Jan 21 22:10:48 BYIZB3 kernel: [   14.056826] IRQ 17/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs

Jan 21 22:10:48 BYIZB3 kernel: [   14.210382] saa7133[0]: i2c eeprom 00: be 16 0d 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
Jan 21 22:10:48 BYIZB3 kernel: [   14.210392] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff 00 01 50 32 79 01 3c ca 50
Jan 21 22:10:48 BYIZB3 kernel: [   14.210400] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 03 01 00 06 ff 00 29 02 51 96 2b
Jan 21 22:10:48 BYIZB3 kernel: [   14.210408] saa7133[0]: i2c eeprom 30: a7 58 7a 1f 03 8e 84 5e da 7a 04 b3 05 87 b2 3c
Jan 21 22:10:48 BYIZB3 kernel: [   14.210416] saa7133[0]: i2c eeprom 40: ff 28 00 c0 96 10 03 00 c0 1c fd 79 44 9f c2 8f
Jan 21 22:10:48 BYIZB3 kernel: [   14.210424] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jan 21 22:10:48 BYIZB3 kernel: [   14.210432] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jan 21 22:10:48 BYIZB3 kernel: [   14.210440] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jan 21 22:10:48 BYIZB3 kernel: [   14.210448] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jan 21 22:10:48 BYIZB3 kernel: [   14.210456] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jan 21 22:10:48 BYIZB3 kernel: [   14.210464] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jan 21 22:10:48 BYIZB3 kernel: [   14.210472] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jan 21 22:10:48 BYIZB3 kernel: [   14.210479] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jan 21 22:10:48 BYIZB3 kernel: [   14.210487] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jan 21 22:10:48 BYIZB3 kernel: [   14.210495] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jan 21 22:10:48 BYIZB3 kernel: [   14.210503] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jan 21 22:10:48 BYIZB3 kernel: [   14.210513] i2c-adapter i2c-0: Invalid 7-bit address 0x7a
Jan 21 22:10:48 BYIZB3 kernel: [   14.268115] tuner 0-004b: chip found @ 0x96 (saa7133[0])
Jan 21 22:10:48 BYIZB3 kernel: [   14.348025] tda829x 0-004b: setting tuner address to 60
Jan 21 22:10:48 BYIZB3 kernel: [   14.420026] tda829x 0-004b: type set to tda8290+75a

Jan 21 22:10:52 BYIZB3 kernel: [   18.384333] saa7133[0]: dsp access error
Jan 21 22:10:52 BYIZB3 kernel: [   18.384335] saa7133[0]: dsp access error
Jan 21 22:10:52 BYIZB3 kernel: [   18.384358] saa7133[0]: dsp access error
Jan 21 22:10:52 BYIZB3 kernel: [   18.384360] saa7133[0]: dsp access error
Jan 21 22:10:52 BYIZB3 kernel: [   18.452096] saa7133[0]: registered device video0 [v4l2]
Jan 21 22:10:52 BYIZB3 kernel: [   18.452120] saa7133[0]: registered device vbi0
Jan 21 22:10:52 BYIZB3 kernel: [   18.455691] saa7134 ALSA driver for DMA sound loaded
Jan 21 22:10:52 BYIZB3 kernel: [   18.455700] IRQ 17/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
Jan 21 22:10:52 BYIZB3 kernel: [   18.455716] saa7133[0]/alsa: saa7133[0] at 0xfddff000 irq 17 registered as card -2
Jan 21 22:10:52 BYIZB3 kernel: [   18.493009] dvb_init() allocating 1 frontend
Jan 21 22:10:52 BYIZB3 kernel: [   18.764672] DVB: registering new adapter (saa7133[0])
Jan 21 22:10:52 BYIZB3 kernel: [   18.764676] DVB: registering adapter 0 frontend 0 (Philips TDA10086 DVB-S)...
```Messages after warm start
```
Jan 21 23:09:25 BYIZB3 kernel: [   14.300490] saa7130/34: v4l2 driver version 0.2.15 loaded
Jan 21 23:09:25 BYIZB3 kernel: [   14.300540] saa7134 0000:02:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 21 23:09:25 BYIZB3 kernel: [   14.300545] saa7133[0]: found at 0000:02:01.0, rev: 209, irq: 17, latency: 84, mmio: 0xfddff000
Jan 21 23:09:25 BYIZB3 kernel: [   14.300550] saa7133[0]: subsystem: 16be:000d, board: Medion Md8800 Quadro [card=96,autodetected]
Jan 21 23:09:25 BYIZB3 kernel: [   14.300561] saa7133[0]: board init: gpio is 0
Jan 21 23:09:25 BYIZB3 kernel: [   14.300566] IRQ 17/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs

Jan 21 23:09:25 BYIZB3 kernel: [   14.452033] saa7133[0]: i2c eeprom 00: be 16 0d 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
Jan 21 23:09:25 BYIZB3 kernel: [   14.452042] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff 00 01 50 32 79 01 3c ca 50
Jan 21 23:09:25 BYIZB3 kernel: [   14.452051] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 03 01 00 06 ff 00 29 02 51 96 2b
Jan 21 23:09:25 BYIZB3 kernel: [   14.452059] saa7133[0]: i2c eeprom 30: a7 58 7a 1f 03 8e 84 5e da 7a 04 b3 05 87 b2 3c
Jan 21 23:09:25 BYIZB3 kernel: [   14.452067] saa7133[0]: i2c eeprom 40: ff 28 00 c0 96 10 03 00 c0 1c fd 79 44 9f c2 8f
Jan 21 23:09:25 BYIZB3 kernel: [   14.452075] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jan 21 23:09:25 BYIZB3 kernel: [   14.452083] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jan 21 23:09:25 BYIZB3 kernel: [   14.452097] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jan 21 23:09:25 BYIZB3 kernel: [   14.452105] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jan 21 23:09:25 BYIZB3 kernel: [   14.452113] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jan 21 23:09:25 BYIZB3 kernel: [   14.452121] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jan 21 23:09:25 BYIZB3 kernel: [   14.452129] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jan 21 23:09:25 BYIZB3 kernel: [   14.452137] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jan 21 23:09:25 BYIZB3 kernel: [   14.452145] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jan 21 23:09:25 BYIZB3 kernel: [   14.452153] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jan 21 23:09:25 BYIZB3 kernel: [   14.452161] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Jan 21 23:09:25 BYIZB3 kernel: [   14.452171] i2c-adapter i2c-0: Invalid 7-bit address 0x7a

Jan 21 23:09:25 BYIZB3 kernel: [   14.469915] hda_codec: Unknown model for ALC1200, trying auto-probe from BIOS...
Jan 21 23:09:25 BYIZB3 kernel: [   14.470162] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
Jan 21 23:09:25 BYIZB3 kernel: [   14.516100] tuner 0-004b: chip found @ 0x96 (saa7133[0])
Jan 21 23:09:25 BYIZB3 kernel: [   14.624144] tda829x 0-004b: setting tuner address to 60

Jan 21 23:09:25 BYIZB3 kernel: [   14.696182] tda829x 0-004b: type set to tda8290+75a

Jan 21 23:09:29 BYIZB3 kernel: [   18.556877] saa7133[0]: dsp access error
Jan 21 23:09:29 BYIZB3 kernel: [   18.556879] saa7133[0]: dsp access error
Jan 21 23:09:29 BYIZB3 kernel: [   18.620069] saa7133[0]: registered device video0 [v4l2]
Jan 21 23:09:29 BYIZB3 kernel: [   18.620094] saa7133[0]: registered device vbi0
Jan 21 23:09:29 BYIZB3 kernel: [   18.623751] saa7134 ALSA driver for DMA sound loaded
Jan 21 23:09:29 BYIZB3 kernel: [   18.623760] IRQ 17/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
Jan 21 23:09:29 BYIZB3 kernel: [   18.623778] saa7133[0]/alsa: saa7133[0] at 0xfddff000 irq 17 registered as card -2
Jan 21 23:09:29 BYIZB3 kernel: [   18.665151] dvb_init() allocating 1 frontend
Jan 21 23:09:29 BYIZB3 kernel: [   18.940288] DVB: registering new adapter (saa7133[0])
Jan 21 23:09:29 BYIZB3 kernel: [   18.940291] DVB: registering adapter 0 frontend 0 (Philips TDA10086 DVB-S)...

```

---

### Post by Rschnauzer on 2010-01-27
Sorry, may nobody help or give some hints?
I now installed additional all packets that may help to use live TV, but I do not know which SW in detail helped.

```
2010-01-23 19:22:44 install alsa-oss <keine> 1.0.17-1
2010-01-23 19:22:45 install faac <keine> 1.26-0.1ubuntu2
2010-01-23 19:22:45 install faad <keine> 2.6.1-3.1
2010-01-23 19:22:45 install flashplugin-nonfree-extrasound <keine> 0.0.svn2431-3
2010-01-23 19:22:45 install libtsmux0 <keine> 0.3.0-1
2010-01-23 19:22:46 install libamrnb3 <keine> 7.0.0.2-0.1medibuntu1
2010-01-23 19:22:46 install libamrwb3 <keine> 7.0.0.3-0.0medibuntu1
2010-01-23 19:22:46 install w32codecs <keine> 20071007-0medibuntu5
2010-01-23 19:22:46 install non-free-codecs <keine> 4medibuntu1
2010-01-23 19:22:47 install sun-java6-fonts <keine> 6-15-1
2010-01-23 19:22:47 install gstreamer0.10-plugins-base-dbg <keine> 0.10.25-2ubuntu1.2
2010-01-23 19:22:47 install gstreamer0.10-plugins-good-dbg <keine> 0.10.16-1ubuntu3
```Now live TV sometimes work with Klear and VLC, but I don´t find how to reproduce the positive start and I don't find messages if it does not work. 

How may I get ubuntu as reliable as MS Vista. If I really want to use the media PC at a certain time I have to boot Vista:mad:.

How may I get more information and a solution on the problem? It may be a timing problem in synchronizing the satellite stream or in initializing the DVB-S card.

---

### Post by Rschnauzer on 2010-01-28
Tryin to start DVB-S I get no tunung lock, does anybody know which additional parameter may help?
```
[0xb7401170] main input debug: creating access 'dvb-s' path='satno=1,frequency=11836000,voltage=18,srate=27500000'
[0x9cb3a98] main access debug: looking for access module: 1 candidate
[0x9cb3a98] dvb access debug: Opening device /dev/dvb/adapter0/frontend0
[0xb7400a10] qt4 interface debug: IM: Setting an input
[0x9cb3a98] dvb access debug: Frontend Info:
[0x9cb3a98] dvb access debug:   name = Philips TDA10086 DVB-S
[0x9cb3a98] dvb access debug:   type = QPSK (DVB-S)
[0x9cb3a98] dvb access debug:   frequency_min = 950000 (kHz)
[0x9cb3a98] dvb access debug:   frequency_max = 2150000 (kHz)
[0x9cb3a98] dvb access debug:   frequency_stepsize = 125
[0x9cb3a98] dvb access debug:   frequency_tolerance = 0
[0x9cb3a98] dvb access debug:   symbol_rate_min = 1000000 (kHz)
[0x9cb3a98] dvb access debug:   symbol_rate_max = 45000000 (kHz)
[0x9cb3a98] dvb access debug:   symbol_rate_tolerance (ppm) = 0
[0x9cb3a98] dvb access debug:   notifier_delay (ms) = 0
[0x9cb3a98] dvb access debug: Frontend Info capability list:
[0x9cb3a98] dvb access debug:   inversion auto
[0x9cb3a98] dvb access debug:   forward error correction 1/2
[0x9cb3a98] dvb access debug:   forward error correction 2/3
[0x9cb3a98] dvb access debug:   forward error correction 3/4
[0x9cb3a98] dvb access debug:   forward error correction 5/6
[0x9cb3a98] dvb access debug:   forward error correction 6/7
[0x9cb3a98] dvb access debug:   forward error correction 7/8
[0x9cb3a98] dvb access debug:   forward error correction auto
[0x9cb3a98] dvb access debug:   card can do QPSK
[0x9cb3a98] dvb access debug: End of capability list
[0x9cb3a98] dvb access debug: trying to tune the frontend...
[0x9cb3a98] dvb access debug: frequency 11836000 is in Ku-band
[0x9cb3a98] dvb access debug: using inversion=2
[0x9cb3a98] dvb access debug: using fec=9
[0x9cb3a98] dvb access debug: using voltage=18
[0x9cb3a98] dvb access debug: using tone=1
[0x9cb3a98] dvb access debug: Opening device /dev/dvb/adapter0/dvr0
[0x9cb3a98] dvb access debug: setting filter on PAT
[0x9cb3a98] dvb access debug: Opening device /dev/dvb/adapter0/demux0
[0x9cb3a98] dvb access debug: DMXSetFilter: DMX_PES_OTHER for PID 0
[0x9cb3a98] dvb access debug: Opening device /dev/dvb/adapter0/ca0
[0x9cb3a98] dvb access warning: CAMInit: opening CAM device failed (No such file or directory)
[0x9cb3a98] main access debug: using access module "dvb"
[0x9cb3a98] main access debug: TIMER module_need() : 745,214 ms - Total 745,214 ms / 1 intvls (Avg 745,214 ms)
[0x9fb51f8] main stream debug: Using AStream*Block
[0x9fb51f8] main stream debug: pre buffering
[0x9fb51f8] main stream debug: received first data after 220 ms
[0x9fb51f8] main stream debug: prebuffering done 188 bytes in 0s - 0 kbytes/s
[0x9de3958] main stream debug: looking for stream_filter module: 4 candidates
[0x9de3958] main stream debug: TIMER module_need() : 0,128 ms - Total 0,128 ms / 1 intvls (Avg 0,128 ms)
[0x9de3958] main stream debug: looking for stream_filter module: 1 candidate
[0x9de3958] main stream debug: using stream_filter module "stream_filter_record"
[0x9de3958] main stream debug: TIMER module_need() : 0,082 ms - Total 0,082 ms / 1 intvls (Avg 0,082 ms)
[0xb7401170] main input debug: creating demux: access='dvb-s' demux='' path='satno=1,frequency=11836000,voltage=18,srate=27500000'
[0x9de3a20] main demux debug: looking for demux module: 51 candidates
[0x9cb3a98] dvb access warning: no lock, tuning again
[0x9cb3a98] dvb access debug: using inversion=2
[0x9cb3a98] dvb access debug: using fec=9
[0x9cb3a98] dvb access debug: using voltage=18
[0x9cb3a98] dvb access debug: using tone=1
[0x9cb3a98] dvb access warning: no lock, tuning again
[0x9cb3a98] dvb access debug: using inversion=2
[0x9cb3a98] dvb access debug: using fec=9
[0x9cb3a98] dvb access debug: using voltage=18
[0x9cb3a98] dvb access debug: using tone=1

```I need help, i can't find any hint in documentation.

---

