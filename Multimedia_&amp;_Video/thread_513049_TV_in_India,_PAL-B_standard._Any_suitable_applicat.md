---
title: "TV in India, PAL-B standard. Any suitable application?"
date: 2007-07-30
forum: Multimedia &amp; Video
---

### Post by mridkash on 2007-07-30
Hi,
I've been trying to configure TVtime and Myth Tv, but none of them have a PAL-B standard setting, which is for cable tv in India.

I get an empty screen saying no signal

TV card: LeadTech WinFast 2000 XP   BrookTree bt878 chipset

dmesg:
[   16.060924] bttv0: Bt878 (rev 17) at 0000:06:01.0, irq: 23, latency: 32, mmio: 0xbf001000
[   16.060940] bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609
[   16.060944] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,insmod option]

[   16.061480] bttv0: using tuner=38
[   16.061486] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   16.062204] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   16.062940] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   16.063656] bttv0: i2c: checking for TDA9887 @ 0x86... found

Please Help, Thanks

*******
Update:
Problem solved using card no 34 and tuner= 41
*******

---

