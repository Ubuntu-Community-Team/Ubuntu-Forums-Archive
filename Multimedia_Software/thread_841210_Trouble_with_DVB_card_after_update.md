---
title: "Trouble with DVB card after update"
date: 2008-06-26
forum: Multimedia Software
---

### Post by Lido on 2008-06-26
I've had a dual KWORLD atsc 115 tuner AMD low watt dual core machine working great for a few months getting OTA HD from my roof antenna. The other day Ubuntu did one of its updates and there was a little "restart required" icon in the upper right corner of the screen. Before I restarted I used Synaptic to get the games SuperTux and SuperTuxCart. After restarting (and possibly just before that) I could no longer watch live tv through Myth. Recordings don't work either actually. They appear to be recording, but when you try to watch them there's an error in the front end saying "file could not be found" or similar. I can watch recordings from before this happened, but those are running out.

There doesn't seem to be anything noteworthy in the front or back end log files.

I scanned for channels for mplayer and got a lot that looked like this but no channels were found:
```
>>> tune to: 605028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 611028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 611028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 617028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 623028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 629028615:8VSB
```

Then in dmesg there's this even though I've never tried to update the firmware in the cards:
```
 30.145935] saa7133[0]: registered device video0 [v4l2]
[   30.145954] saa7133[0]: registered device vbi0
[   30.146432] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 17
[   30.146442] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [LNKC] -> GSI 17 (level, low) -> IRQ 17
[   30.146450] saa7133[1]: found at 0000:01:0a.0, rev: 209, irq: 17, latency: 32, mmio: 0xfebfe800
[   30.146457] saa7133[1]: subsystem: 17de:7352, board: Kworld ATSC110 [card=90,insmod option]
[   30.146469] saa7133[1]: board init: gpio is 100
[   30.287758] saa7133[1]: i2c eeprom 00: de 17 52 73 ff ff ff ff ff ff ff ff ff ff ff ff
[   30.287764] saa7133[1]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.287771] saa7133[1]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.287777] saa7133[1]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.287783] saa7133[1]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.287789] saa7133[1]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.287796] saa7133[1]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.287802] saa7133[1]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.323332] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   30.330818] saa7133[1]: registered device video1 [v4l2]
[   30.330833] saa7133[1]: registered device vbi1
[   30.330906] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.19  Wed Sep 12 14:08:38 PDT 2007
[   30.343355] saa7134 ALSA driver for DMA sound loaded
[   30.343394] saa7133[0]/alsa: saa7133[0] at 0xfebff000 irq 18 registered as card -2
[   30.343721] saa7133[1]/alsa: saa7133[1] at 0xfebfe800 irq 17 registered as card -1
[   30.475221] nxt200x: NXT2004 Detected
[   30.475252] DVB: registering new adapter (saa7133[0]).
[   30.475256] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   30.483230] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   30.497716] nxt2004: Waiting for firmware upload(2)...
[   30.497720] nxt2004: No firmware uploaded (timeout or file not found?)
[   30.507200] nxt200x: NXT2004 Detected
[   30.507237] DVB: registering new adapter (saa7133[1]).
[   30.507240] DVB: registering frontend 1 (Nextwave NXT200X VSB/QAM frontend)...
[   30.515207] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   30.517395] nxt2004: Waiting for firmware upload(2)...
[   30.517400] nxt2004: No firmware uploaded (timeout or file not found?)

[   51.028988] nxt200x: Timeout waiting for nxt200x to stop. This is ok after firmware upload.
[   51.132914] nxt200x: Error writing multireg register 0x08
[   51.172886] nxt200x: Error writing multireg register 0x08
[   51.324782] nxt200x: Error writing multireg register 0x80
[   51.396749] nxt200x: Error writing multireg register 0x08
[   51.468684] nxt200x: Error writing multireg register 0x08
[   51.540642] nxt200x: Error writing multireg register 0x80
[   51.580619] nxt200x: Error writing multireg register 0x81
[   51.620580] nxt200x: Error writing multireg register 0x82
[   51.692529] nxt200x: Error writing multireg register 0x88
[   51.764480] nxt200x: Error writing multireg register 0x80
[   52.340338] nxt200x: Timeout waiting for nxt2004 to init.
[   53.135520] nxt200x: Timeout waiting for nxt200x to stop. This is ok after firmware upload.
[   53.239448] nxt200x: Error writing multireg register 0x08
[   53.279420] nxt200x: Error writing multireg register 0x08
[   53.431316] nxt200x: Error writing multireg register 0x80
[   53.503266] nxt200x: Error writing multireg register 0x08
[   53.575216] nxt200x: Error writing multireg register 0x08
[   53.647167] nxt200x: Error writing multireg register 0x80
[   53.687140] nxt200x: Error writing multireg register 0x81
[   53.727112] nxt200x: Error writing multireg register 0x82
[   53.799064] nxt200x: Error writing multireg register 0x88
[   53.871016] nxt200x: Error writing multireg register 0x80
[   54.178801] nxt200x: Timeout waiting for nxt2004 to init.
[   54.438623] nxt200x: Timeout waiting for nxt2004 to init.
[   56.205640] nxt200x: Timeout waiting for nxt2004 to init.
[   56.381517] nxt200x: Timeout waiting for nxt2004 to init.
[   76.236864] NET: Registered protocol family 17
[   77.246856] wlan0: Initial auth_alg=0

```

---

### Post by Lido on 2008-06-26
This fixed it. I guess there was a kernel update and the firmware got left behind:
```
sudo cp /lib/firmware/2.6.22-14-generic/*nxt* /lib/firmware/2.6.22-15-generic/
```

---

### Post by Kepesk on 2008-10-26
I would appear to have a similar issue with the same card, but getting my hands on the old version of the firmware has proven very difficult; scripts included with old kernels simply download new versions of the nxt2004 firmware from the website.

Might someone be able to provide the old firmware, or point me to a place where I might find it?

Thanks!

---

### Post by laceration on 2008-11-30
Thanks Lido, I had the same problem with kernal-headers update from 2.6.24.21 to 22.  One small note, a reboot is necessary too. 

why do the thank you buttons disappear after time?

---

