---
title: "Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast"
date: 2011-05-31
forum: Multimedia Software
---

### Post by genux05 on 2011-05-31
Has anyone had any luck with this device to work ? 

From the lspci 

```

09:04.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
	Subsystem: Avermedia Technologies Inc M115 DVB-T, PAL/SECAM/NTSC Tuner
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at d2005000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [40] Power Management version 2
	Kernel driver in use: saa7134
	Kernel modules: saa7134

```

dmesg shows that is has been loaded but the tuner does not appear to work ?

```


saa7134 0000:09:04.0: enabling device (0000 -> 0002)
[   26.263748] saa7134 0000:09:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.263756] saa7133[0]: found at 0000:09:04.0, rev: 209, irq: 16, latency: 0, mmio: 0xd2005000
[   26.263764] saa7134 0000:09:04.0: setting latency timer to 64
[   26.263769] saa7133[0]: subsystem: 1461:a836, board: Avermedia M115 [card=138,autodetected]
[   26.263787] saa7133[0]: board init: gpio is a400000
[   26.328561] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   26.328628] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   26.328663] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   26.543990] saa7133[0]: i2c eeprom 00: 61 14 36 a8 00 00 00 00 00 00 00 00 00 00 00 00
[   26.544002] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   26.544012] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 01 03 08 ff 00 c0 ff ff ff ff
[   26.544022] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.544031] saa7133[0]: i2c eeprom 40: ff 65 00 ff c2 1e ff ff ff ff ff ff ff ff ff ff
[   26.544041] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.544051] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.544060] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.544070] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.544079] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.544089] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.544099] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.544109] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.544118] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.544128] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.544138] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   26.570037] saa7133[0]: i2c scan: found device @ 0xa0  [eeprom]
[   26.604000] saa7133[0]: i2c scan: found device @ 0xc2  [???]
[   26.612195] i2c-core: driver [tuner] using legacy suspend method
[   26.612198] i2c-core: driver [tuner] using legacy resume method
[   26.630125] tuner 0-0061: chip found @ 0xc2 (saa7133[0])
[   26.632728] xc2028 0-0061: creating new instance
[   26.632731] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
[   26.991795] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.991805] nvidia 0000:01:00.0: setting latency timer to 64

```

Firmware does not appear to load for the tuner ?

```

[   97.600208] xc2028 0-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000.
[   97.600401] xc2028 0-0061: i2c output error: rc = -5 (should be 64)
[   97.600404] xc2028 0-0061: -5 returned from send
[   97.600407] xc2028 0-0061: Error -22 while loading base firmware
[   97.660037] xc2028 0-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000.
[   97.660230] xc2028 0-0061: i2c output error: rc = -5 (should be 64)
[   97.660232] xc2028 0-0061: -5 returned from send
[   97.660235] xc2028 0-0061: Error -22 while loading base firmware
[   97.660505] xc2028 0-0061: Error on line 1200: -5
[  110.152127] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[  119.445810] exe (2441): /proc/2441/oom_adj is deprecated, please use /proc/2441/oom_score_adj instead.
[  123.627058] xc2028 0-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000.
[  123.627252] xc2028 0-0061: i2c output error: rc = -5 (should be 64)
[  123.627254] xc2028 0-0061: -5 returned from send
[  123.627258] xc2028 0-0061: Error -22 while loading base firmware
[  123.680057] xc2028 0-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000.
[  123.680255] xc2028 0-0061: i2c output error: rc = -5 (should be 64)
[  123.680257] xc2028 0-0061: -5 returned from send
[  123.680261] xc2028 0-0061: Error -22 while loading base firmware
[  123.680558] xc2028 0-0061: Error on line 1200: -5
[  139.478946] xc2028 0-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000.
[  139.479147] xc2028 0-0061: i2c output error: rc = -5 (should be 64)
[  139.479152] xc2028 0-0061: -5 returned from send
[  139.479158] xc2028 0-0061: Error -22 while loading base firmware
[  139.530086] xc2028 0-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000.
[  139.530287] xc2028 0-0061: i2c output error: rc = -5 (should be 64)
[  139.530292] xc2028 0-0061: -5 returned from send
[  139.530298] xc2028 0-0061: Error -22 while loading base firmware
[  150.044868] xc2028 0-0061: Error on line 1200: -5
[  178.277348] xc2028 0-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000.
[  178.277542] xc2028 0-0061: i2c output error: rc = -5 (should be 64)
[  178.277544] xc2028 0-0061: -5 returned from send
[  178.277547] xc2028 0-0061: Error -22 while loading base firmware
[  178.330264] xc2028 0-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000.
[  178.330465] xc2028 0-0061: i2c output error: rc = -5 (should be 64)
[  178.330470] xc2028 0-0061: -5 returned from send
[  178.330476] xc2028 0-0061: Error -22 while loading base firmware
[  186.252625] xc2028 0-0061: Error on line 1200: -5
[ 1652.490062] CE: hpet increased min_delta_ns to 20113 nsec


```

any advice / help at all ?

---

### Post by genux05 on 2011-05-31
Forgot to say that my laptop is a Acer Aspire 9815WKHi Desktop Replacement Laptop.

---

### Post by no2498 on 2011-05-31
[http://www.google.com/search?client=opera&rls=en&q=Multimedia+controller:+Philips+Semiconductors+SAA7131/SAA7133/SAA7135+Video+Broadcast&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest](http://www.google.com/search?client=opera&rls=en&q=Multimedia+controller:+Philips+Semiconductors+SAA7131/SAA7133/SAA7135+Video+Broadcast&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest)

what program you using to see if it works

---

### Post by genux05 on 2011-06-01
hi no2498

I was using tvtime, but just was saying no signal.

Thanks

---

### Post by bance on 2011-06-02
have you tried linux-firmware-nonfree from synaptic ?

---

### Post by genux05 on 2011-06-06
hi bance

Yeah, have tried the nonfree firmware, but did not seem to work.

I think that I have come to the conclusion that it may not work in 64bit mode ? compared to 32 bit ? I am sure that about a year ago it was working when I was trying out a 32 bit version of the ubuntu on the laptop.

would there be any difference between a 32bit sys file (for the xc3038 extraction tool) for usage on a 64bit system ?

thanks..

---

