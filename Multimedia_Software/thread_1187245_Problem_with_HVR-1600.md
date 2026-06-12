---
title: "Problem with HVR-1600"
date: 2009-06-14
forum: Multimedia Software
---

### Post by joker35 on 2009-06-14
Hi,

I have a problem getting a tuner card HVR-1600 to work in Mythbuntu.

My MB is ASUS M2NBP-VM and having onboard NVidia graphis I increased vmalloc to 256M.

I did a fresh install with 9.04 but the output I get from 
dmesg | grep cx18 is this:

[   10.095729] cx18:  Start initialization, version 1.0.1
[   10.098754] cx18-0: Initializing card #0
[   10.098758] cx18-0: Autodetected Hauppauge card
[   10.100263] cx18 0000:04:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   10.100272] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   10.103023] cx18-0: cx23418 revision 01010000 (B)
[   10.328702] cx18-0: Autodetected Hauppauge HVR-1600
[   10.328704] cx18-0: VBI is not yet supported
[   10.442489] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   10.442544] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   10.484920] cx18-0: Disabled encoder IDX device
[   10.485026] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   10.485030] DVB: registering new adapter (cx18)
[   10.505811] cx18-0: frontend initialization failed
[   10.506012] cx18-0: DVB failed to register
[   10.506079] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   10.506138] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   10.506391] cx18-0: Error -1 registering devices
[   10.506911] cx18-0: Error -1 on initialization
[   10.506924] cx18: probe of 0000:04:09.0 failed with error -1
[   10.506980] cx18:  End initialization

What could be wrong?

Thx

---

