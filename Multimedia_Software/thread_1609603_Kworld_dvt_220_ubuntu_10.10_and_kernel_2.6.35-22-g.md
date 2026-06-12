---
title: "Kworld dvt 220 ubuntu 10.10 and kernel 2.6.35-22-generic"
date: 2010-10-30
forum: Multimedia Software
---

### Post by turkosbon on 2010-10-30
Hello i update my update 10.10 when i did this, my kworld dvb-t 220 doesn't work in Me TV

> 
Linux 2.6.35-22-generic #35-Ubuntu SMP


dmesg | grep saa

> 
[   15.524623] saa7130/34: v4l2 driver version 0.2.16 loaded
[   15.528659] saa7134 0000:03:07.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   15.528664] saa7133[0]: found at 0000:03:07.0, rev: 209, irq: 17, latency: 32, mmio: 0xfdfff000
[   15.528670] saa7133[0]: subsystem: 17de:7201, board: Tevion/KWorld DVB-T 220RF [card=88,autodetected]
[   15.528689] saa7133[0]: board init: gpio is 100
[   15.700029] saa7133[0]: i2c eeprom 00: de 17 01 72 ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700035] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700041] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700046] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700052] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700057] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700063] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700069] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700074] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700080] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700085] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700091] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700097] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700102] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700108] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700113] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.820128] tuner 1-004b: chip found @ 0x96 (saa7133[0])
[   21.810262] saa7133[0]: dsp access error
[   21.950088] saa7133[0]: registered device video0 [v4l2]
[   21.950114] saa7133[0]: registered device vbi0
[   21.950143] saa7133[0]: registered device radio0
[   21.954726] saa7134 ALSA driver for DMA sound loaded
[   21.954756] saa7133[0]/alsa: saa7133[0] at 0xfdfff000 irq 17 registered as card -2
[   22.900091] DVB: registering new adapter (saa7133[0])



lspci -vvv

> 
03:07.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
    Subsystem: KWorld Computer Co. Ltd. Device 7201
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (63750ns min, 63750ns max)
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at fdfff000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: saa7134
    Kernel modules: saa7134


Thanks you.

---

### Post by xc3RnbFO8P on 2010-10-30
In Terminal:
> sudo modprobe saa7134-dvb
do dmesg again or start Me-tv

---

### Post by turkosbon on 2010-10-30
i put "sudo modprobe saa7134-dvb"
> 
[   15.524623] saa7130/34: v4l2 driver version 0.2.16 loaded
[   15.528659] saa7134 0000:03:07.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   15.528664] saa7133[0]: found at 0000:03:07.0, rev: 209, irq: 17, latency: 32, mmio: 0xfdfff000
[   15.528670] saa7133[0]: subsystem: 17de:7201, board: Tevion/KWorld DVB-T 220RF [card=88,autodetected]
[   15.528689] saa7133[0]: board init: gpio is 100
[   15.700029] saa7133[0]: i2c eeprom 00: de 17 01 72 ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700035] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700041] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700046] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700052] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700057] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700063] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700069] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700074] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700080] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700085] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700091] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700097] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700102] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700108] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.700113] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.820128] tuner 1-004b: chip found @ 0x96 (saa7133[0])
[   21.810262] saa7133[0]: dsp access error
[   21.950088] saa7133[0]: registered device video0 [v4l2]
[   21.950114] saa7133[0]: registered device vbi0
[   21.950143] saa7133[0]: registered device radio0
[   21.954726] saa7134 ALSA driver for DMA sound loaded
[   21.954756] saa7133[0]/alsa: saa7133[0] at 0xfdfff000 irq 17 registered as card -2
[   22.900091] DVB: registering new adapter (saa7133[0])
[27101.010091] DVB: registering new adapter (saa7133[0])


in Me TV in't work

---

### Post by xc3RnbFO8P on 2010-10-30
Try to run Me-tv in Terminal  and show the output:
> me-tv

---

### Post by turkosbon on 2010-10-30
i try with
me-tv -v --disable-epg-thread

> 
Me TV 1.3.1
30/10/10 22:27:01: Application constructor
30/10/10 22:27:01: sqlite3_threadsafe() = 1
30/10/10 22:27:01: Database 'exists' 
30/10/10 22:27:01: Opening database file '/home/tomas/.local/share/me-tv/me-tv.db'
30/10/10 22:27:01: Loading UI files
30/10/10 22:27:01: Application constructed
30/10/10 22:27:01: Initialising table 'version'
30/10/10 22:27:01: Required Database version: 6
30/10/10 22:27:01: Actual Database version: 6
30/10/10 22:27:01: Me TV database initialised
30/10/10 22:27:01: StatusIcon constructor started
30/10/10 22:27:01: StatusIcon constructed
30/10/10 22:27:01: MainWindow constructor
30/10/10 22:27:01: MainWindow constructed
30/10/10 22:27:01: Scanning DVB devices ...
30/10/10 22:27:01: Opening frontend device: /dev/dvb/adapter0/frontend0
30/10/10 22:27:06: Device: 'Philips TDA10046H DVB-T' (DVB-T) at "/dev/dvb/adapter0/frontend0"
30/10/10 22:27:06: Loading channels ...
30/10/10 22:27:06: Loading channel 'La 1'
30/10/10 22:27:06: Channel 'La 1' added
30/10/10 22:27:06: Loading channel 'La 2'
30/10/10 22:27:06: Channel 'La 2' added
30/10/10 22:27:06: Loading channel 'ANTENA 3'
30/10/10 22:27:06: EPG Event 542 (La cara más divertidaTit. originalTit.Tit. orig. cap.) (CHANNEL: 44) (sábado, 30 octubre 2010, 11:30) version 13 added
30/10/10 22:27:06: Channel 'ANTENA 3' added
30/10/10 22:27:06: Loading channel 'CUATRO'
30/10/10 22:27:06: Channel 'CUATRO' added
30/10/10 22:27:06: Loading channel 'Telecinco'
30/10/10 22:27:06: Channel 'Telecinco' added
30/10/10 22:27:06: Loading channel 'laSexta'
30/10/10 22:27:06: Channel 'laSexta' added
30/10/10 22:27:06: Loading channel 'Boing'
30/10/10 22:27:06: Channel 'Boing' added
30/10/10 22:27:06: Loading channel 'Telecinco HD'
30/10/10 22:27:06: Channel 'Telecinco HD' added
30/10/10 22:27:06: Loading channel 'MTV'
30/10/10 22:27:06: Channel 'MTV' added
30/10/10 22:27:06: Loading channel 'La 10'
30/10/10 22:27:06: Channel 'La 10' added
30/10/10 22:27:06: Loading channel 'Punto Radio'
30/10/10 22:27:06: Channel 'Punto Radio' added
30/10/10 22:27:06: Loading channel 'TVE-HD Pruebas'
30/10/10 22:27:06: Channel 'TVE-HD Pruebas' added
30/10/10 22:27:06: Loading channel 'Teledeporte'
30/10/10 22:27:06: Channel 'Teledeporte' added
30/10/10 22:27:06: Loading channel 'Radio Clásica'
30/10/10 22:27:06: Channel 'Radio Clásica' added
30/10/10 22:27:06: Loading channel 'Radio 3'
30/10/10 22:27:06: Channel 'Radio 3' added
30/10/10 22:27:06: Loading channel 'CANAL 6 TEIDEVISION'
30/10/10 22:27:06: Channel 'CANAL 6 TEIDEVISION' added
30/10/10 22:27:06: Loading channel 'ELDIA TV'
30/10/10 22:27:06: Channel 'ELDIA TV' added
30/10/10 22:27:06: Loading channel 'Radio El Dia'
30/10/10 22:27:06: Channel 'Radio El Dia' added
30/10/10 22:27:06: Loading channel '24h'
30/10/10 22:27:06: Channel '24h' added
30/10/10 22:27:06: Loading channel 'Clan'
30/10/10 22:27:06: Channel 'Clan' added
30/10/10 22:27:06: Loading channel 'RNE1'
30/10/10 22:27:06: Channel 'RNE1' added
30/10/10 22:27:06: Loading channel 'RNEC'
30/10/10 22:27:06: Channel 'RNEC' added
30/10/10 22:27:06: Loading channel 'RNE3'
30/10/10 22:27:06: Channel 'RNE3' added
30/10/10 22:27:06: Loading channel 'Canal Ingenieria'
30/10/10 22:27:06: Channel 'Canal Ingenieria' added
30/10/10 22:27:06: Loading channel 'VEO7'
30/10/10 22:27:06: Channel 'VEO7' added
30/10/10 22:27:06: Loading channel 'AXN'
30/10/10 22:27:06: Channel 'AXN' added
30/10/10 22:27:06: Loading channel 'Tienda en VEO'
30/10/10 22:27:06: Channel 'Tienda en VEO' added
30/10/10 22:27:06: Loading channel 'GUIDE PLUS+'
30/10/10 22:27:06: Channel 'GUIDE PLUS+' added
30/10/10 22:27:06: Loading channel 'Intereconomía'
30/10/10 22:27:06: Channel 'Intereconomía' added
30/10/10 22:27:06: Loading channel 'Radio Intereconomía'
30/10/10 22:27:06: Channel 'Radio Intereconomía' added
30/10/10 22:27:06: Loading channel 'esRadio'
30/10/10 22:27:06: Channel 'esRadio' added
30/10/10 22:27:06: Loading channel 'Unknown Service 834000-65534'
30/10/10 22:27:06: Channel 'Unknown Service 834000-65534' added
30/10/10 22:27:06: Loading channel 'RADIO MARCA'
30/10/10 22:27:06: Channel 'RADIO MARCA' added
30/10/10 22:27:06: Loading channel 'Vaughan Radio'
30/10/10 22:27:06: Channel 'Vaughan Radio' added
30/10/10 22:27:06: Loading channel 'CNN+'
30/10/10 22:27:06: Channel 'CNN+' added
30/10/10 22:27:06: Loading channel 'CANAL+ Dos'
30/10/10 22:27:06: Channel 'CANAL+ Dos' added
30/10/10 22:27:06: Loading channel 'CANAL CLUB'
30/10/10 22:27:06: Channel 'CANAL CLUB' added
30/10/10 22:27:06: Loading channel 'SER'
30/10/10 22:27:06: Channel 'SER' added
30/10/10 22:27:06: Loading channel '40 PRINCIPALES'
30/10/10 22:27:06: Channel '40 PRINCIPALES' added
30/10/10 22:27:06: Loading channel 'CADENA DIAL'
30/10/10 22:27:06: Channel 'CADENA DIAL' added
30/10/10 22:27:06: Loading channel 'FDF'
30/10/10 22:27:06: Channel 'FDF' added
30/10/10 22:27:06: Loading channel 'LaSiete'
30/10/10 22:27:06: Channel 'LaSiete' added
30/10/10 22:27:06: Loading channel 'Disney Channel'
30/10/10 22:27:06: Channel 'Disney Channel' added
30/10/10 22:27:06: Loading channel 'Cincoshop'
30/10/10 22:27:06: Channel 'Cincoshop' added
30/10/10 22:27:06: Loading channel 'NEOX'
30/10/10 22:27:06: EPG Event 19585 (Cine: Shin Chan, operación rescateTit. originalInt.Tit. orig. cap.Tit.) (CHANNEL: 45) (sábado, 30 octubre 2010, 11:00) version 23 added
30/10/10 22:27:06: Channel 'NEOX' added
30/10/10 22:27:06: Loading channel 'NOVA'
30/10/10 22:27:06: EPG Event 24048 (Manos a la obraNúm. cap.Tit.Tit. originalTit. orig. cap.) (CHANNEL: 46) (sábado, 30 octubre 2010, 09:45) version 21 added
30/10/10 22:27:06: EPG Event 24049 (Las VegasTit.Núm. cap.Tit. originalTit. orig. cap.) (CHANNEL: 46) (sábado, 30 octubre 2010, 12:00) version 21 added
30/10/10 22:27:06: EPG Event 24089 (Punto de miraTit. orig. cap.Tit.Tit. original) (CHANNEL: 46) (lunes, 01 noviembre 2010, 06:45) version 1 added
30/10/10 22:27:06: EPG Event 24090 (El futuro en tus manosTit.Tit. originalTit. orig. cap.) (CHANNEL: 46) (lunes, 01 noviembre 2010, 07:30) version 1 added
30/10/10 22:27:06: EPG Event 24091 (¿Qué me pasa Doctor?Núm. cap.Tit. orig. cap.Tit.Tit. original) (CHANNEL: 46) (lunes, 01 noviembre 2010, 09:00) version 1 added
30/10/10 22:27:06: EPG Event 24092 (Champs 12Núm. cap.Tit.Tit. orig. cap.Tit. original) (CHANNEL: 46) (lunes, 01 noviembre 2010, 09:30) version 1 added
30/10/10 22:27:06: EPG Event 24093 (Tormeta en el paraísoTit.Tit. orig. cap.Tit. original) (CHANNEL: 46) (lunes, 01 noviembre 2010, 10:15) version 1 added
30/10/10 22:27:06: EPG Event 24094 (La traiciónTit. originalTit.Tit. orig. cap.) (CHANNEL: 46) (lunes, 01 noviembre 2010, 11:00) version 1 added
30/10/10 22:27:06: EPG Event 24095 (LalolaNúm. cap.Tit. orig. cap.Tit. originalTit.) (CHANNEL: 46) (lunes, 01 noviembre 2010, 12:00) version 1 added
30/10/10 22:27:06: EPG Event 24096 (Cocina con Bruno OteizaTit. originalTit.Tit. orig. cap.) (CHANNEL: 46) (lunes, 01 noviembre 2010, 13:00) version 1 added
30/10/10 22:27:06: EPG Event 24097 (Karlos Arguiñano en tu cocinaTit. orig. cap.Tit. originalTit.) (CHANNEL: 46) (lunes, 01 noviembre 2010, 13:30) version 1 added
30/10/10 22:27:06: EPG Event 24098 (Esta casa era una ruina EE.UUTit.Tit. orig. cap.Tit. original) (CHANNEL: 46) (lunes, 01 noviembre 2010, 14:00) version 1 added
30/10/10 22:27:06: EPG Event 24099 (Pasión de GavilanesTit.Tit. originalTit. orig. cap.) (CHANNEL: 46) (lunes, 01 noviembre 2010, 15:00) version 1 added
30/10/10 22:27:06: EPG Event 24100 (¿Dónde está Elisa?Tit. orig. cap.Tit. originalTit.) (CHANNEL: 46) (lunes, 01 noviembre 2010, 15:45) version 1 added
30/10/10 22:27:06: EPG Event 24101 (La viuda de blancoTit. originalTit.Tit. orig. cap.) (CHANNEL: 46) (lunes, 01 noviembre 2010, 17:00) version 1 added
30/10/10 22:27:06: EPG Event 24102 (La TormentaTit.Tit. originalTit. orig. cap.) (CHANNEL: 46) (lunes, 01 noviembre 2010, 18:15) version 1 added
30/10/10 22:27:06: EPG Event 24103 (La dama de TroyaTit.Tit. orig. cap.Tit. original) (CHANNEL: 46) (lunes, 01 noviembre 2010, 19:15) version 1 added
30/10/10 22:27:06: EPG Event 24104 (Cine: Patch AdamsTit. originalTit.Tit. orig. cap.) (CHANNEL: 46) (lunes, 01 noviembre 2010, 21:15) version 1 added
30/10/10 22:27:06: EPG Event 24105 (Las VegasTit. originalNúm. cap.Tit. orig. cap.Tit.) (CHANNEL: 46) (lunes, 01 noviembre 2010, 23:30) version 1 added
30/10/10 22:27:06: EPG Event 24106 (AstroshowTit.Tit. orig. cap.Tit. original) (CHANNEL: 46) (martes, 02 noviembre 2010, 00:30) version 1 added
30/10/10 22:27:06: Channel 'NOVA' added
30/10/10 22:27:06: Loading channel 'ONDA CERO'
30/10/10 22:27:06: Channel 'ONDA CERO' added
30/10/10 22:27:06: Loading channel 'EUROPA FM'
30/10/10 22:27:06: Channel 'EUROPA FM' added
30/10/10 22:27:06: Loading channel 'ONDA MELODÍA'
30/10/10 22:27:06: Channel 'ONDA MELODÍA' added
30/10/10 22:27:06: Loading channel 'GOL TELEVISIÓN'
30/10/10 22:27:06: EPG Event 32483 (Preview Show Premier 2010/2011) (CHANNEL: 50) (sábado, 30 octubre 2010, 11:30) version 25 added
30/10/10 22:27:06: EPG Event 32484 (Liga Escocesa 2010/2011 J10) (CHANNEL: 50) (sábado, 30 octubre 2010, 12:00) version 25 added
30/10/10 22:27:06: EPG Event 32485 (La Liga Show 2010/2011) (CHANNEL: 50) (sábado, 30 octubre 2010, 14:00) version 25 added
30/10/10 22:27:06: EPG Event 32486 (Preview Show Premier 2010/2011) (CHANNEL: 50) (sábado, 30 octubre 2010, 14:30) version 25 added
30/10/10 22:27:06: EPG Event 32487 (Liga Inglesa 2010/2011 J10) (CHANNEL: 50) (sábado, 30 octubre 2010, 15:00) version 25 added
30/10/10 22:27:06: EPG Event 32488 (Liga Española 2010/2011 J09) (CHANNEL: 50) (sábado, 30 octubre 2010, 17:00) version 25 added
30/10/10 22:27:06: EPG Event 32489 (Liga Española 2010/2011 J09) (CHANNEL: 50) (sábado, 30 octubre 2010, 19:00) version 25 added
30/10/10 22:27:06: EPG Event 32490 (Directo Gol Sábado 30/10/2010) (CHANNEL: 50) (sábado, 30 octubre 2010, 20:55) version 25 added
30/10/10 22:27:06: EPG Event 32491 (Liga Portuguesa 2010/2011 J09) (CHANNEL: 50) (sábado, 30 octubre 2010, 21:15) version 25 added
30/10/10 22:27:06: EPG Event 32492 (Directo Gol Sábado 30/10/2010) (CHANNEL: 50) (sábado, 30 octubre 2010, 23:15) version 25 added
30/10/10 22:27:06: EPG Event 32493 (Liga Española 2010/2011 J09) (CHANNEL: 50) (domingo, 31 octubre 2010, 00:00) version 25 added
30/10/10 22:27:06: EPG Event 32494 (Liga Francesa 2010/2011 J11) (CHANNEL: 50) (domingo, 31 octubre 2010, 00:50) version 25 added
30/10/10 22:27:06: EPG Event 32495 (Goles Liga BBVA 2010/2011 v1) (CHANNEL: 50) (domingo, 31 octubre 2010, 01:40) version 25 added
30/10/10 22:27:06: EPG Event 32496 (Liga Escocesa 2010/2011 J10) (CHANNEL: 50) (domingo, 31 octubre 2010, 02:10) version 25 added
30/10/10 22:27:06: EPG Event 32497 (Goles Liga BBVA 2010/2011 v1) (CHANNEL: 50) (domingo, 31 octubre 2010, 04:00) version 25 added
30/10/10 22:27:06: EPG Event 32498 (Premier World Show 2010/2011) (CHANNEL: 50) (domingo, 31 octubre 2010, 04:30) version 25 added
30/10/10 22:27:06: EPG Event 32499 (Goles Liga BBVA 2010/2011 v1) (CHANNEL: 50) (domingo, 31 octubre 2010, 05:00) version 25 added
30/10/10 22:27:06: EPG Event 32500 (Liga Francesa 2010/2011 J11) (CHANNEL: 50) (domingo, 31 octubre 2010, 05:30) version 25 added
30/10/10 22:27:06: EPG Event 32501 (Goles Liga BBVA 2010/2011 v1) (CHANNEL: 50) (domingo, 31 octubre 2010, 07:15) version 25 added
30/10/10 22:27:06: EPG Event 32502 (Liga Inglesa 2010/2011 J10) (CHANNEL: 50) (domingo, 31 octubre 2010, 07:45) version 25 added
30/10/10 22:27:06: EPG Event 32503 (Liga Inglesa 2010/2011 J10) (CHANNEL: 50) (domingo, 31 octubre 2010, 09:35) version 25 added
30/10/10 22:27:06: EPG Event 32504 (Goles Liga BBVA 2010/2011 v1) (CHANNEL: 50) (domingo, 31 octubre 2010, 11:30) version 25 added
30/10/10 22:27:06: EPG Event 32505 (Liga Inglesa 2010/2011 J10) (CHANNEL: 50) (domingo, 31 octubre 2010, 12:00) version 25 added
30/10/10 22:27:06: EPG Event 32506 (Liga Inglesa 2010/2011 J10) (CHANNEL: 50) (domingo, 31 octubre 2010, 13:30) version 25 added
30/10/10 22:27:06: EPG Event 32507 (Goles Liga BBVA 2010/2011 v1) (CHANNEL: 50) (domingo, 31 octubre 2010, 15:30) version 25 added
30/10/10 22:27:06: EPG Event 32508 (Liga Española Segunda Division 2010/2011 J10) (CHANNEL: 50) (domingo, 31 octubre 2010, 16:00) version 25 added
30/10/10 22:27:06: EPG Event 32509 (Liga Española 2010/2011 J09) (CHANNEL: 50) (domingo, 31 octubre 2010, 18:00) version 25 added
30/10/10 22:27:06: EPG Event 32510 (Liga Francesa 2010/2011 J11) (CHANNEL: 50) (domingo, 31 octubre 2010, 20:00) version 25 added
30/10/10 22:27:06: EPG Event 32511 (Directo Gol Domingo 31/10/2010) (CHANNEL: 50) (domingo, 31 octubre 2010, 22:00) version 25 added
30/10/10 22:27:06: EPG Event 32512 (Liga Española 2010/2011 J09) (CHANNEL: 50) (domingo, 31 octubre 2010, 23:20) version 25 added
30/10/10 22:27:06: EPG Event 32513 (Premier World Show 2010/2011) (CHANNEL: 50) (lunes, 01 noviembre 2010, 00:15) version 25 added
30/10/10 22:27:06: EPG Event 32514 (Liga Belga 2010/2011 J13) (CHANNEL: 50) (lunes, 01 noviembre 2010, 00:50) version 25 added
30/10/10 22:27:06: EPG Event 32515 (Premier World Show 2010/2011) (CHANNEL: 50) (lunes, 01 noviembre 2010, 02:40) version 25 added
30/10/10 22:27:06: EPG Event 32516 (Liga Belga 2010/2011 J13) (CHANNEL: 50) (lunes, 01 noviembre 2010, 03:10) version 25 added
30/10/10 22:27:06: EPG Event 32517 (Premier World Show 2010/2011) (CHANNEL: 50) (lunes, 01 noviembre 2010, 05:00) version 25 added
30/10/10 22:27:06: EPG Event 32518 (Liga Escocesa 2010/2011 J10) (CHANNEL: 50) (lunes, 01 noviembre 2010, 05:30) version 25 added
30/10/10 22:27:06: EPG Event 32519 (Goles Liga BBVA 2010/2011 Jornada completa) (CHANNEL: 50) (lunes, 01 noviembre 2010, 07:20) version 25 added
30/10/10 22:27:06: EPG Event 32520 (Liga Española Segunda Division 2010/2011 J10) (CHANNEL: 50) (lunes, 01 noviembre 2010, 07:45) version 25 added
30/10/10 22:27:06: EPG Event 32521 (Premier World Show 2010/2011) (CHANNEL: 50) (lunes, 01 noviembre 2010, 08:30) version 25 added
30/10/10 22:27:06: EPG Event 32522 (Directo Gol Domingo 31/10/2010) (CHANNEL: 50) (lunes, 01 noviembre 2010, 09:00) version 25 added
30/10/10 22:27:06: EPG Event 32523 (Highlights Liga Francesa 2010/2011) (CHANNEL: 50) (lunes, 01 noviembre 2010, 10:15) version 25 added
30/10/10 22:27:06: EPG Event 32524 (Highlights Liga Inglesa 2010/2011) (CHANNEL: 50) (lunes, 01 noviembre 2010, 11:10) version 25 added
30/10/10 22:27:06: EPG Event 32525 (Especial Informativo Gol) (CHANNEL: 50) (lunes, 01 noviembre 2010, 12:00) version 25 added
30/10/10 22:27:06: EPG Event 32526 (Goles Liga BBVA 2010/2011 v2) (CHANNEL: 50) (lunes, 01 noviembre 2010, 12:30) version 25 added
30/10/10 22:27:06: EPG Event 32527 (GOL NOTICIAS mediodía.) (CHANNEL: 50) (lunes, 01 noviembre 2010, 13:00) version 25 added
30/10/10 22:27:06: EPG Event 32528 (Champions League Magazine 2010/2011) (CHANNEL: 50) (lunes, 01 noviembre 2010, 14:00) version 25 added
30/10/10 22:27:06: EPG Event 32529 (Goles Liga BBVA 2010/2011 Jornada completa) (CHANNEL: 50) (lunes, 01 noviembre 2010, 14:30) version 25 added
30/10/10 22:27:06: EPG Event 32530 (GOL NOTICIAS 16:00) (CHANNEL: 50) (lunes, 01 noviembre 2010, 15:00) version 25 added
30/10/10 22:27:06: EPG Event 32531 (Liga Inglesa 2010/2011 J10) (CHANNEL: 50) (lunes, 01 noviembre 2010, 15:15) version 25 added
30/10/10 22:27:06: EPG Event 32532 (GOL NOTICIAS 18:00) (CHANNEL: 50) (lunes, 01 noviembre 2010, 17:00) version 25 added
30/10/10 22:27:06: EPG Event 32533 (Especial Informativo Gol) (CHANNEL: 50) (lunes, 01 noviembre 2010, 17:30) version 25 added
30/10/10 22:27:06: EPG Event 32534 (Champions League Magazine 2010/2011) (CHANNEL: 50) (lunes, 01 noviembre 2010, 18:00) version 25 added
30/10/10 22:27:06: EPG Event 32535 (Goles Liga BBVA 2010/2011 v2) (CHANNEL: 50) (lunes, 01 noviembre 2010, 18:30) version 25 added
30/10/10 22:27:06: EPG Event 32536 (MUNDO GOL TARDE) (CHANNEL: 50) (lunes, 01 noviembre 2010, 19:00) version 25 added
30/10/10 22:27:06: EPG Event 32537 (Liga Española 2010/2011 J09) (CHANNEL: 50) (lunes, 01 noviembre 2010, 20:00) version 25 added
30/10/10 22:27:06: EPG Event 32538 (MUNDO GOL CLUB) (CHANNEL: 50) (lunes, 01 noviembre 2010, 22:00) version 25 added
30/10/10 22:27:06: EPG Event 32539 (Goles Liga BBVA 2010/2011 Jornada completa) (CHANNEL: 50) (lunes, 01 noviembre 2010, 23:00) version 25 added
30/10/10 22:27:06: EPG Event 32540 (Highlights Copa Sudamericana 2010) (CHANNEL: 50) (lunes, 01 noviembre 2010, 23:30) version 25 added
30/10/10 22:27:06: EPG Event 32541 (Liga Inglesa 2010/2011 J10) (CHANNEL: 50) (martes, 02 noviembre 2010, 00:00) version 25 added
30/10/10 22:27:06: EPG Event 32542 (Liga Colombiana 2010/2 J16) (CHANNEL: 50) (martes, 02 noviembre 2010, 01:50) version 25 added
30/10/10 22:27:06: EPG Event 32543 (Liga Ecuatoriana 2010/2 J18) (CHANNEL: 50) (martes, 02 noviembre 2010, 03:40) version 25 added
30/10/10 22:27:06: EPG Event 32544 (Liga Belga 2010/2011 J13) (CHANNEL: 50) (martes, 02 noviembre 2010, 05:30) version 25 added
30/10/10 22:27:06: EPG Event 32545 (Goles Liga Adelante 2010/2011 Versión Completa) (CHANNEL: 50) (martes, 02 noviembre 2010, 07:20) version 25 added
30/10/10 22:27:06: EPG Event 32546 (Liga Española Segunda Division 2010/2011 J10) (CHANNEL: 50) (martes, 02 noviembre 2010, 07:45) version 25 added
30/10/10 22:27:06: EPG Event 32547 (Goles Liga Adelante 2010/2011 Versión Completa) (CHANNEL: 50) (martes, 02 noviembre 2010, 08:30) version 25 added
30/10/10 22:27:06: EPG Event 32548 (MUNDO GOL CLUB) (CHANNEL: 50) (martes, 02 noviembre 2010, 09:00) version 25 added
30/10/10 22:27:06: EPG Event 32549 (Champions League Magazine 2010/2011) (CHANNEL: 50) (martes, 02 noviembre 2010, 10:00) version 25 added
30/10/10 22:27:06: EPG Event 32550 (Liga Española 2010/2011 J09) (CHANNEL: 50) (martes, 02 noviembre 2010, 10:25) version 25 added
30/10/10 22:27:06: EPG Event 32551 (Liga Inglesa 2010/2011 J10) (CHANNEL: 50) (martes, 02 noviembre 2010, 11:15) version 25 added
30/10/10 22:27:06: EPG Event 32552 (GOL NOTICIAS mediodía.) (CHANNEL: 50) (martes, 02 noviembre 2010, 13:00) version 25 added
30/10/10 22:27:06: EPG Event 32553 (Planeta Axel) (CHANNEL: 50) (martes, 02 noviembre 2010, 14:00) version 25 added
30/10/10 22:27:06: EPG Event 32554 (Champions League Magazine 2010/2011) (CHANNEL: 50) (martes, 02 noviembre 2010, 14:30) version 25 added
30/10/10 22:27:06: EPG Event 32555 (GOL NOTICIAS 16:00) (CHANNEL: 50) (martes, 02 noviembre 2010, 15:00) version 25 added
30/10/10 22:27:06: EPG Event 32556 (Gol Zap) (CHANNEL: 50) (martes, 02 noviembre 2010, 15:15) version 25 added
30/10/10 22:27:06: EPG Event 32557 (Highlights Liga Inglesa 2010/2011) (CHANNEL: 50) (martes, 02 noviembre 2010, 15:45) version 25 added
30/10/10 22:27:06: EPG Event 32558 (Champions League Magazine 2010/2011) (CHANNEL: 50) (martes, 02 noviembre 2010, 16:30) version 25 added
30/10/10 22:27:06: EPG Event 32559 (MUNDO GOL TARDE) (CHANNEL: 50) (martes, 02 noviembre 2010, 17:00) version 25 added
30/10/10 22:27:06: EPG Event 32560 (Liga de Campeones 2010/2011 Fase de Grupos J04) (CHANNEL: 50) (martes, 02 noviembre 2010, 17:30) version 25 added
30/10/10 22:27:06: EPG Event 32561 (MUNDO GOL TARDE) (CHANNEL: 50) (martes, 02 noviembre 2010, 19:25) version 25 added
30/10/10 22:27:06: EPG Event 32562 (Liga de Campeones 2010/2011 Fase de Grupos J04) (CHANNEL: 50) (martes, 02 noviembre 2010, 19:45) version 25 added
30/10/10 22:27:06: EPG Event 32563 (Goles Champions League 2010/2011) (CHANNEL: 50) (martes, 02 noviembre 2010, 21:40) version 25 added
30/10/10 22:27:06: EPG Event 32564 (MUNDO GOL CLUB) (CHANNEL: 50) (martes, 02 noviembre 2010, 22:15) version 25 added
30/10/10 22:27:06: EPG Event 32565 (Liga de Campeones 2010/2011 Fase de Grupos J04) (CHANNEL: 50) (martes, 02 noviembre 2010, 23:15) version 25 added
30/10/10 22:27:06: Channel 'GOL TELEVISIÓN' added
30/10/10 22:27:06: Channels loaded
30/10/10 22:27:06: Creating stream manager
30/10/10 22:27:06: Creating frontend thread
30/10/10 22:27:06: Thread 'Frontend' created
30/10/10 22:27:06: Creating FrontendThread (/dev/dvb/adapter0/frontend0)
30/10/10 22:27:06: Opening frontend device '/dev/dvb/adapter0/dvr0' for reading ...
30/10/10 22:27:06: FrontendThread created (/dev/dvb/adapter0/frontend0)
30/10/10 22:27:06: Starting frontend thread
30/10/10 22:27:06: Starting frontend thread (/dev/dvb/adapter0/frontend0)
30/10/10 22:27:06: Waiting for 'Frontend' to start
30/10/10 22:27:06: Frontend thread running (/dev/dvb/adapter0/frontend0)
30/10/10 22:27:06: Entering FrontendThread loop (/dev/dvb/adapter0/frontend0)
30/10/10 22:27:06: Thread 'Frontend' started
30/10/10 22:27:06: Loading scheduled recordings
30/10/10 22:27:06: Scheduled recordings loaded
30/10/10 22:27:06: Setting geometry (0, 24, 1918, 1002)
30/10/10 22:27:07: Last channel '12' found
30/10/10 22:27:07: Not currently displaying 'Teledeporte'
30/10/10 22:27:07: Selected idle frontend 'Philips TDA10046H DVB-T' for display
30/10/10 22:27:07: StreamManager stopping display
30/10/10 22:27:07: Stopping frontend thread (/dev/dvb/adapter0/frontend0)
30/10/10 22:27:07: Thread 'Frontend' marked for termination
30/10/10 22:27:07: Thread 'Frontend' waiting for join ...
30/10/10 22:27:07: FrontendThread loop exited (/dev/dvb/adapter0/frontend0)
30/10/10 22:27:07: Thread 'Frontend' exited
30/10/10 22:27:07: Thread 'Frontend' joined
30/10/10 22:27:07: Frontend thread stopped and joined (/dev/dvb/adapter0/frontend0)
30/10/10 22:27:07: Starting frontend thread (/dev/dvb/adapter0/frontend0)
30/10/10 22:27:07: Waiting for 'Frontend' to start
30/10/10 22:27:07: Frontend thread running (/dev/dvb/adapter0/frontend0)
30/10/10 22:27:07: Entering FrontendThread loop (/dev/dvb/adapter0/frontend0)
30/10/10 22:27:07: Thread 'Frontend' started
30/10/10 22:27:07: FrontendThread::start_display(Teledeporte)
30/10/10 22:27:07: Stopping frontend thread (/dev/dvb/adapter0/frontend0)
30/10/10 22:27:07: Thread 'Frontend' marked for termination
30/10/10 22:27:07: Thread 'Frontend' waiting for join ...
30/10/10 22:27:07: FrontendThread loop exited (/dev/dvb/adapter0/frontend0)
30/10/10 22:27:07: Thread 'Frontend' exited
30/10/10 22:27:07: Thread 'Frontend' joined
30/10/10 22:27:07: Frontend thread stopped and joined (/dev/dvb/adapter0/frontend0)
30/10/10 22:27:07: Creating new stream output
30/10/10 22:27:07: Creating MPEG stream
30/10/10 22:27:07: Added new channel stream 'Teledeporte' -> '/home/tomas/.me-tv/me-tv.fifo'
30/10/10 22:27:07: Removing demuxers
30/10/10 22:27:07: Frontend::tune_to(666000000)
30/10/10 22:27:07: Waiting for signal lock ...
30/10/10 22:27:09: Got signal lock
30/10/10 22:27:09: Demuxer::set_filter(0,0,255)
30/10/10 22:27:14: Exception: Read timeout
30/10/10 22:27:16: Message Dialog: 'Read timeout'
30/10/10 22:27:16: Updating EPG
30/10/10 22:27:16: EPG update complete



---

### Post by xc3RnbFO8P on 2010-10-30
Try **Kaffeine**

---

### Post by turkosbon on 2010-10-30
> **Ringi said:**
> Try **Kaffeine**

doesn't work

---

### Post by turkosbon on 2010-10-31
I' sorry, i start windows xp and doesn't work. i open my computer quit and put the kworld , work now. i don't happen.

---

### Post by xc3RnbFO8P on 2010-10-31
Nothing to be sorry about, you found a solution to fix it :)

---

