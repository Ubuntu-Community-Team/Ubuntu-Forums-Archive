---
title: "Tv Tuner Card Bttv Match Please Help"
date: 2007-02-23
forum: Multimedia &amp; Video
---

### Post by cile on 2007-02-23
I have TV Tuner card Match bttv and does not work on Ubuntu 6.10. I have tried everithing I know, I dont know too much, and it doesn work. When I dmesg I get this:

[17179592.236000] bttv: driver version 0.9.16 loaded
[17179592.236000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179592.236000] bttv: Bt8xx card found (0).
[17179592.236000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179592.236000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179592.236000] bttv0: Bt878 (rev 17) at 0000:02:02.0, irq: 11, latency: 32, mmio: 0xde100000
[17179592.236000] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[17179592.236000] bttv0: gpio: en=00000000, out=00000000 in=003fffff [init]
[17179592.240000] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[17179592.240000] bttv0: using tuner=-1
[17179592.240000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179592.244000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179592.248000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179592.248000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179592.252000] bttv0: registered device video0
[17179592.252000] bttv0: registered device vbi0
[17179592.284000] bt878: AUDIO driver version 0.0.0 loaded
[17179592.284000] bt878: Bt878 AUDIO function found (0).
[17179592.284000] ACPI: PCI Interrupt 0000:02:02.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179592.284000] bt878_probe: card id=[0x0],[ <NULL> ] has DVB functions.
[17179592.284000] bt878(0): Bt878 (rev 17) at 02:02.1, irq: 11, latency: 32, memory: 0xde101000

Please HELP ME

---

### Post by david_2001 on 2007-02-27
It would be helpful if you posted the manufacturer and full model name/number of your TV card.  In the meantime, the best place to start looking for information about using TV cards under GNU/Linux is the [COLOR="SandyBrown"][LinuxTV]("http://linuxtv.org/")[/COLOR] site.

---

### Post by tarm0 on 2008-01-03
I also have problems with my Match tv card (in gutsy 2.6.22.14-rt). On the card chip is written "Conexant Fusion 878A 25878-13". When I open Zapping I can see only one channel (Eurosport) in black and white without sound. If I try to open Edit - Channels or Edit - Preferences, Zapping shuts down (same when opened in terminal). Tvtime shuts down immediately after opening.

my dmesg:

[   43.514076] Linux video capture interface: v2.00
[   43.737999] bttv: driver version 0.9.17 loaded
[   43.738004] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   43.738612] bttv: Bt8xx card found (0).
[   43.738725] bttv0: Bt878 (rev 17) at 0000:02:05.0, irq: 17, latency: 32, mmio: 0xefbfe000
[   43.738735] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   43.738763] bttv0: gpio: en=00000000, out=00000000 in=007fffff [init]
[   43.740007] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[   43.740011] bttv0: using tuner=-1
[   43.740013] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   43.742249] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   43.742940] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   43.743487] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   43.744817] bttv0: registered device video0
[   43.745146] bttv0: registered device vbi0
[   43.788094] bt878: AUDIO driver version 0.0.0 loaded
[   43.789755] bt878: Bt878 AUDIO function found (0).
[   43.789779] bt878_probe: card id=[0x0], Unknown card.
[   43.789780] Exiting..
[   43.789787] bt878: probe of 0000:02:05.1 failed with error -22

---

