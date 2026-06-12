---
title: "KWorld 115 ATSC with mythtv help"
date: 2008-01-16
forum: Multimedia &amp; Video
---

### Post by Lido on 2008-01-16
I think I've read every thread on this card, but I can't get it working. I only want to use it to record OTA ATSC channels so I only put the line ```
modprobe saa7134-dvb
``` in /etc/modules. I have two of them installed by the way, but I've just been trying to set up one of them in mythtv at first.

I've got the file dvb-fe-nxt2004.fw in /lib/modules.

I set up a file here as suggested in the mythtv kworld 110 wiki and in a few threads:
```
$ more /etc/modprobe.d/kworld_atsc_115 
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=90,90 disable_ir=1

```

In mythtv-setup, under Card type, I selected: DVB DTV capture card (v3.x) and below on the same page it says:```
Frontend ID: Nextwave NXT200X VSB/QAM frontend Subtype: ATSC
```

Under video sources I have Schedules Direct set up. Under Input Connections the card is set up as follows:```

Capture Device [DVB : 0]            Input:     DVBInput
Video source:Schedules Direct
```

When I click "Fetch channels from listings source" nothing seems to happen, so I scan for channels with the following settings:```

Video Source: Schedules Direct      Capture Card: [DVB : 0]
Scan Type: Full Scan
Frequency Table: Broadcast
ATSC Modulation: Terrestrial (8-VSB)
Channel Separator: (5_1) Underscore
Existing Channel Treatment: Minimal Updates
```

When I hit next I get "no lock" and timeouts when it's searching for channels regardless of which input I have the antenna connected to. The signal strength is 99% regardless of whether or not the antenna is plugged in and the signal/noise is around 91%.

It looks like the card is being found ok. From dmesg:
```
[   37.889225] saa7133[0]: found at 0000:01:08.0, rev: 209, irq: 18, latency: 32, mmio: 0xfebff000
[   37.889231] saa7133[0]: subsystem: 17de:7352, board: Kworld ATSC110 [card=90,insmod option]
[   37.889241] saa7133[0]: board init: gpio is 100
[   37.968469] lirc_dev: IR Remote Control driver registered, at major 61 
[   37.970082] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: Driver for Soundgraph iMON MultiMedian IR/VFD, v0.3
[   37.970087] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: Venky Raju <dev@venky.ws>
[   37.970134] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_probe: found IMON device
[   37.970141] lirc_dev: lirc_register_plugin: sample_rate: 0
[   37.970177] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_probe: Registered iMON plugin (minor:0)
[   37.970224] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_probe: iMON device on usb<3:2> initialized
[   37.970238] usbcore: registered new interface driver lirc_imon
[   38.032559] saa7133[0]: i2c eeprom 00: de 17 52 73 ff ff ff ff ff ff ff ff ff ff ff ff
[   38.032568] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.032575] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.032581] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.032587] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.032594] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.032600] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.032606] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.063326] parport_pc 00:05: reported by Plug and Play ACPI
[   38.063381] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   38.112506] tuner 0-0061: chip found @ 0xc2 (saa7133[0])
[   38.112540] tuner 0-0061: type set to 68 (Philips TUV1236D ATSC/NTSC dual in)
[   38.112543] tuner 0-0061: type set to 68 (Philips TUV1236D ATSC/NTSC dual in)
[   38.140407] saa7133[0]: registered device video0 [v4l2]
[   38.140437] saa7133[0]: registered device vbi0
[   38.140933] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 17
[   38.140944] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [LNKC] -> GSI 17 (level, low) -> IRQ 17
[   38.140952] saa7133[1]: found at 0000:01:0a.0, rev: 209, irq: 17, latency: 32, mmio: 0xfebfe800
[   38.140958] saa7133[1]: subsystem: 17de:7352, board: Kworld ATSC110 [card=90,insmod option]
[   38.140967] saa7133[1]: board init: gpio is 100
[   38.284378] saa7133[1]: i2c eeprom 00: de 17 52 73 ff ff ff ff ff ff ff ff ff ff ff ff
[   38.284386] saa7133[1]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.284393] saa7133[1]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.284399] saa7133[1]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.284405] saa7133[1]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.284411] saa7133[1]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.284417] saa7133[1]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.284422] saa7133[1]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.331538] saa7133[1]: registered device video1 [v4l2]
[   38.331564] saa7133[1]: registered device vbi1
[   38.352428] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   38.352434] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LAZA] -> GSI 21 (level, low) -> IRQ 21
[   38.353250] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   38.380877] saa7134 ALSA driver for DMA sound loaded
[   38.380904] saa7133[0]/alsa: saa7133[0] at 0xfebff000 irq 18 registered as card -2
[   38.381131] saa7133[1]/alsa: saa7133[1] at 0xfebfe800 irq 17 registered as card -1
[   38.416323] nxt200x: NXT2004 Detected
[   38.416391] DVB: registering new adapter (saa7133[0]).
[   38.416395] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   38.424290] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   38.454788] ieee80211_init: failed to initialize WME (err=-17)
[   38.467688] nxt2004: Waiting for firmware upload(2)...
[   38.481106] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   38.481149] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   38.481187] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   38.481245] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   38.496665] wmaster0: Selected rate control algorithm 'simple'
[   38.610122] usbcore: registered new interface driver rt73usb
[   38.612864] usbcore: registered new interface driver rt2500usb
[   38.644414] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   39.626082] lp0: using parport0 (interrupt-driven).
[   39.726626] Adding 1951888k swap on /dev/sda3.  Priority:-1 extents:1 across:1951888k
[   40.167087] nxt2004: Firmware upload complete
[   41.994095] nxt200x: NXT2004 Detected
[   41.994127] DVB: registering new adapter (saa7133[1]).
[   41.994131] DVB: registering frontend 1 (Nextwave NXT200X VSB/QAM frontend)...
[   42.006105] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   42.008540] nxt2004: Waiting for firmware upload(2)...
[   43.708924] nxt2004: Firmware upload complete

```

lspci:
```
01:08.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
01:0a.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

```

mythbackend.log:
```
2008-01-15 23:19:46.038 TVRec(4): Changing from WatchingLiveTV to None
2008-01-15 23:19:46.078 Finished recording : channel 4294967295
2008-01-15 23:19:49.001 MainServer::HandleAnnounce Playback
2008-01-15 23:19:49.002 adding: MythTV as a client (events: 0)
2008-01-15 23:19:49.015 TVRec(4): Changing from None to WatchingLiveTV
2008-01-15 23:19:49.016 TVRec(4) Error: Problem finding starting channel, setting to default of '3'.
2008-01-15 23:19:49.018 TVRec(4): HW Tuner: 4->4
2008-01-15 23:19:49.064 Channel(/dev/video0) Error: SetInputAndFormat(6, ATSC) 
                        while setting format (v4l v2)
                        eno: Invalid argument (22)
2008-01-15 23:19:49.088 Channel(/dev/video0): SetInputAndFormat(6, ATSC) 
                        Setting video mode with v4l version 1 worked
2008-01-15 23:19:49.090 GetChannelData() failed because it could not
                        find channel number '3' in DB for source '1'.
2008-01-15 23:19:49.102 TVRec(4) Error: Failed to set channel to 3.
2008-01-15 23:19:49.104 TVRec(4) Error: GetProgramRingBufferForLiveTV()
                        ProgramInfo is invalid.
ProgramInfo: channame() startts(Tue Jan 15 23:19:49 2008) endts(Tue Jan 15 23:19:49 2008)
             recstartts(Tue Jan 15 23:19:49 2008) recendts(Tue Jan 15 23:19:49 2008)
             title()
2008-01-15 23:19:49.122 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:49.180 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:49.236 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:49.292 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:49.348 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:49.404 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:49.460 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:49.516 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:49.572 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:49.628 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:49.684 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:49.740 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:49.796 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:49.852 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:49.908 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:49.964 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:50.020 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:50.076 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:50.132 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:50.188 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:50.244 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:50.300 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:50.356 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:50.412 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:50.468 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:50.524 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:50.580 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:50.636 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:50.692 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:50.748 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:50.804 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:50.860 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:50.916 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:50.972 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:51.028 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:51.084 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:51.140 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:51.196 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:51.252 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:51.308 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:51.364 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:51.420 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:51.476 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:51.532 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:51.588 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:51.644 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:51.700 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:51.756 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:51.812 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:51.868 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:51.924 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:51.980 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:52.036 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:52.092 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:52.148 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:52.204 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:52.260 pcHDTV::GetSignal_v4l1(fd 19, input 6, v4l2): error(Invalid argument)
2008-01-15 23:19:52.277 TVRec(4): Changing from WatchingLiveTV to None
2008-01-15 23:19:52.319 Finished recording : channel 4294967295
2008-01-16 00:24:02.756 Using runtime prefix = /usr
2008-01-16 00:24:02.775 New DB connection, total: 1
2008-01-16 00:24:02.781 Connected to database 'mythconverg' at host: localhost
2008-01-16 00:24:02.784 Current Schema Version: 1160
Starting up as the master server.
2008-01-16 00:24:02.795 New DB connection, total: 2
2008-01-16 00:24:02.796 Connected to database 'mythconverg' at host: localhost
2008-01-16 00:24:02.798 EITHelper: localtime offset -8:00:00 
2008-01-16 00:24:02.802 TVRec(7) Error: Problem finding starting channel, setting to default of '3'.
2008-01-16 00:24:02.804 New DB connection, total: 3
2008-01-16 00:24:02.805 Connected to database 'mythconverg' at host: localhost
2008-01-16 00:24:02.808 GetChannelData() failed because it could not
                        find channel number '3' in DB for source '1'.
2008-01-16 00:24:02.823 DVBChan(0) Error: SetChannelByString(3): Failed to initialize channel options
2008-01-16 00:24:02.823 TVRec(7) Error: Setting start channel '3' failed, 
                        and no other channels were found on input.
2008-01-16 00:24:02.829 New DB scheduler connection
2008-01-16 00:24:02.836 Connected to database 'mythconverg' at host: localhost
2008-01-16 00:24:04.211 Main::Registering HttpStatus Extension
2008-01-16 00:24:04.212 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-01-16 00:24:04.214 Enabled verbose msgs:  important general
2008-01-16 00:24:04.215 AutoExpire: Found 1 recorders w/max rate of 138 MiB/min
2008-01-16 00:24:04.217 AutoExpire: Required Free Space: 3.0 GB w/freq: 10 min
2008-01-16 00:24:04.847 Reschedule requested for id -1.
2008-01-16 00:24:04.859 Scheduled 0 items in 0.0 = 0.00 match + 0.01 place
2008-01-16 00:24:04.866 Seem to be woken up by USER
2008-01-16 00:24:22.854 Expiring  from Tue Jan 15 23:19:07 2008, 0 MBytes, forced expire (LiveTV recording)
2008-01-16 00:24:22.855 Expiring  from Tue Jan 15 23:19:49 2008, 0 MBytes, forced expire (LiveTV recording)
2008-01-16 00:30:20.476 Using runtime prefix = /usr
2008-01-16 00:30:20.489 New DB connection, total: 1
2008-01-16 00:30:20.513 Connected to database 'mythconverg' at host: localhost
2008-01-16 00:30:20.517 Current Schema Version: 1160
Starting up as the master server.
2008-01-16 00:30:20.524 New DB connection, total: 2
2008-01-16 00:30:20.526 Connected to database 'mythconverg' at host: localhost
2008-01-16 00:30:20.528 EITHelper: localtime offset -8:00:00 
2008-01-16 00:30:20.531 TVRec(7) Error: Problem finding starting channel, setting to default of '3'.
2008-01-16 00:30:20.533 New DB connection, total: 3
2008-01-16 00:30:20.535 Connected to database 'mythconverg' at host: localhost
2008-01-16 00:30:20.537 GetChannelData() failed because it could not
                        find channel number '3' in DB for source '1'.
2008-01-16 00:30:20.538 DVBChan(0) Error: SetChannelByString(3): Failed to initialize channel options
2008-01-16 00:30:20.539 TVRec(7) Error: Setting start channel '3' failed, 
                        and no other channels were found on input.
2008-01-16 00:30:20.543 New DB scheduler connection
2008-01-16 00:30:20.544 Connected to database 'mythconverg' at host: localhost
2008-01-16 00:30:21.898 Main::Registering HttpStatus Extension
2008-01-16 00:30:21.900 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-01-16 00:30:21.900 Enabled verbose msgs:  important general
2008-01-16 00:30:21.901 AutoExpire: Found 1 recorders w/max rate of 138 MiB/min
2008-01-16 00:30:21.903 AutoExpire: Required Free Space: 3.0 GB w/freq: 10 min
2008-01-16 00:30:22.550 Reschedule requested for id -1.
2008-01-16 00:30:22.560 Scheduled 0 items in 0.0 = 0.00 match + 0.01 place
2008-01-16 00:30:22.568 Seem to be woken up by USER
```

---

### Post by Lido on 2008-01-16
bump

---

### Post by Lido on 2008-01-17
Anyone?

---

### Post by thecoolcat on 2008-01-17
Couple of recommendations:
1) Make sure you have connected an antenna to the correct input. For me, it was the last input (or the first input depending on ow you look at the card.) (I'm assuming you get decent OTA ATSC signal in where you have your PC.
2) Don't worry about schedule direct first. You can set it up later. Make sure you are able to scan channels and that you could watch them first.
3) Try watching OTA ATSC using mplayer. (This will at least prove that there's no problem with the card.) mythtv uses mplayer as its engine. Here's how I got it to watch it on mplayer:
[http://ubuntuforums.org/showpost.php?p=3994301&postcount=7](http://ubuntuforums.org/showpost.php?p=3994301&postcount=7)
For complete details you can refer here: [http://www.linuxtv.org/wiki/index.php/MPlayer](http://www.linuxtv.org/wiki/index.php/MPlayer)
4) I can post some screenshots late tonight if you need.

---

### Post by Lido on 2008-01-17
Thanks. I will give the mplayer test a try tonight. You can wait on the screen shots. I'll post again here if I can't get the channels to scan after making sure mplayer works. Thanks.

---

### Post by Lido on 2008-01-18
Is the atsc input the one closest to the MB or furthest? I'm getting tuning failed on both inputs.

```
$ /usr/bin/scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > /home/lido/.mplayer/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
>>> tune to: 57028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 57028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 63028615:8VSB
WARNING: >>> tuning failed!!!
ERROR: interrupted by SIGINT, dumping partial result...
dumping lists (0 services)
Done.
$ mplayer dvb://
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) X2 Dual Core Processor BE-2400 (Family: 15, Model: 107, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory

Playing dvb://.
DVB CONFIGURATION IS EMPTY, exit
Failed to open dvb://.
Exiting... (End of file)

```

---

### Post by thecoolcat on 2008-01-18
The tuning failed message is perfectly normal. You are getting this because there are many channels allocated for US OTA ATSC broadcast, but only 10 or so of them would be in service from your local station (for which you'd have decent strength). In the end you should see those active channels in the channels.conf. And the ATSC input is the furthest from the MB (the last input).

---

### Post by Lido on 2008-01-20
Wow, thanks. I got the mplayer to work with dvb, but then I couldn't get mythtv to scan channels. Then I did some more reading and saw it mentioned in the docs that if you're having trouble with your capture card to delete it and try again. I did that and got it working! Very cool. Now I've got to figure out how to get rid of the striping around the edges of moving objects on the screen and get sound working. For the striping I'm going to try to get my nvidia card to output 1080i instead of 1080p and see if that helps. Thanks again, your posts in this thread and elsewhere helped me a lot.

---

