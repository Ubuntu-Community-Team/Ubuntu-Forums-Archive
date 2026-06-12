---
title: "saa7134-dvb module and two tuner cards..."
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by nray on 2008-02-17
Do I need to do anything special to support two AverTVHD A180 tuner cards at the same time?  I followed the directions and had no trouble getting one working, but the other one doesn't even show up, and I get the impression it should just be recognized and work alongside the other.

I'm running Ubuntu 7.10, I used the get_dvb_firmware script to grab the latest firmware, have the saa7134-dvb module load at boot.

Going through the output in dmesg, the only questionable part is this:

[ 32.894438] PCI: Probing PCI hardware (bus 00) 
[ 32.895834] PCI: device 0000:05:00.0 has unknown header type 7f, ignoring. 

Could that perhaps be the card that isn't working?  (maybe there's a hardware problem?)

I'm going to try pulling them both out and swapping what PCI slots they are in (unfortunately there are only two PCI slots in the motherboard I'm using, so I can do little other than swap them).

Anyone have any ideas what the problem might be, or what else I should try next?

---

### Post by nray on 2008-02-18
I pulled one card, and swapped the other one into it's slot, and dmesg output changed to this:

[   44.114380] saa7133[0]: found at 0000:05:01.0, rev: 255, irq: 255, latency: 255, mmio: 0x0
[   44.114386] saa7133[0]: subsystem: ffff:ffff, board: UNKNOWN/GENERIC [card=0,autodetected]
[   44.114389] saa7133[0]: can't get MMIO memory @ 0x0
[   44.114394] saa7134: probe of 0000:05:01.0 failed with error -16
[   44.217379] saa7134 ALSA driver for DMA sound loaded
[   44.217382] saa7134 ALSA: no saa7134 cards found

So I pulled that card, put the other one into the same slot, and got this:

[   43.383969] saa7130/34: v4l2 driver version 0.2.14 loaded
[   43.384021] ACPI: PCI Interrupt 0000:05:01.0[A] -> GSI 17 (level, low) -> IRQ 17
[   43.384029] saa7133[0]: found at 0000:05:01.0, rev: 209, irq: 17, latency: 64, mmio: 0xfebff800
[   43.384036] saa7133[0]: subsystem: 1461:1044, board: AVerMedia AVerTVHD MCE A180 [card=75,autodetected]
[   43.384044] saa7133[0]: board init: gpio is 10400
[   43.517414] saa7133[0]: i2c eeprom 00: 61 14 44 10 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   43.517424] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 00 00 00 00 00 00 00 00 00 00
[   43.517432] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 ff 01 03 06 ff 01 11 00 00 00 00
[   43.517440] saa7133[0]: i2c eeprom 30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   43.517448] saa7133[0]: i2c eeprom 40: ff 64 00 c2 14 16 ff ff 00 00 00 00 00 00 00 00
[   43.517455] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   43.517463] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   43.517471] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   43.520138] saa7133[0]: registered device video0 [v4l2]
[   43.520328] saa7133[0]: registered device vbi0
[   43.529455] saa7134 ALSA driver for DMA sound loaded
[   43.529718] saa7133[0]/alsa: saa7133[0] at 0xfebff800 irq 17 registered as card -2
[   43.653275] nxt200x: NXT2004 Detected
[   43.653317] DVB: registering new adapter (saa7133[0]).
[   43.653322] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   43.661258] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   43.693861] nxt2004: Waiting for firmware upload(2)...
[   45.239074] nxt2004: Firmware upload complete

So looks like I've got a bad card.

---

### Post by steefjeqv on 2008-02-19
Hi,

You can try the following command (in terminal) :

sudo modprobe saa7134-dvb card=75

Try this with the "buggy" card first.

Greetings,
Steven

---

### Post by mteppo on 2008-05-06
> **steefjeqv said:**
> Hi,

You can try the following command (in terminal) :

sudo modprobe saa7134-dvb card=75

Try this with the "buggy" card first.

Greetings,
Steven

I also had the issue that HVR-1110 would not get proper MMIO.
I got around that by swapping the cards about as I already had conexant based NOVA-T.
I have ASUS M2N-VM HDMI (with only 2 PCI slots).
I tried just the one card in "outer slot" (numbered 01:07.0) in lspci - NOVA-T works there but HVR1110 does not. There is something wrong with the card, motherboard, firmware or the PCI enumeration. Or the combination of all mentioned plus some phase-of-the-moon.

Actually - still no luck. I get  "frontend initialization failed"
Now dmesg spits out following:
```
[   30.599260] saa7130/34: v4l2 driver version 0.2.14 loaded
[   30.599762] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 19
[   30.599772] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [LNKA] -> GSI 19 (level, low) -> IRQ 19
[   30.599779] saa7133[0]: found at 0000:01:06.0, rev: 209, irq: 19, latency: 64, mmio: 0xdffff800
[   30.599785] saa7133[0]: subsystem: 0070:6701, board: Hauppauge WinTV-HVR1110 DVB-T/Hybrid [card=104,autodetected]
[   30.599793] saa7133[0]: board init: gpio is 6400000
[   30.611254] cx2388x cx88-mpeg Driver Manager version 0.0.6 loaded
[   30.637045] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0811
[   30.637069] usbcore: registered new interface driver usblp
[   30.637072] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   30.642881] cx2388x v4l2 driver version 0.0.6 loaded
[   30.737330] input: HVR 1110 as /class/input/input4
[   30.737372] ir-kbd-i2c: HVR 1110 detected at i2c-0/0-0071/ir0 [saa7133[0]]
[   30.789198] saa7133[0]: i2c eeprom 00: 70 00 01 67 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   30.789207] saa7133[0]: i2c eeprom 10: ff ff ff 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[   30.789213] saa7133[0]: i2c eeprom 20: 01 40 01 32 32 01 01 33 88 ff 00 aa ff ff ff ff
[   30.789219] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.789225] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 15 60 ff ff ff ff ff ff
[   30.789231] saa7133[0]: i2c eeprom 50: ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   30.789237] saa7133[0]: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   30.789241] saa7133[0]: i2c eeprom 70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   30.803479] saa7133[0]: registered device video0 [v4l2]
[   30.803508] saa7133[0]: registered device vbi0
[   30.803537] saa7133[0]: registered device radio0
[   30.803451] CORE cx88[0]: subsystem: 0070:9002, board: Hauppauge Nova-T DVB-T [card=18,autodetected]
[   30.803457] TV tuner 4 at 0x1fe, Radio tuner -1 at 0x1fe
[   30.827106] saa7134 ALSA driver for DMA sound loaded
[   30.827137] saa7133[0]/alsa: saa7133[0] at 0xdffff800 irq 19 registered as card -2
[   30.860229] saa7133[0]/dvb: frontend initialization failed
[   30.951475] tveeprom 1-0050: Hauppauge model 90003, rev C2B0, serial# 3621363
[   30.951480] tveeprom 1-0050: MAC address is 00-0D-FE-37-41-F3
[   30.951482] tveeprom 1-0050: tuner model is Thompson DTT75105 (idx 110, type 4)
[   30.951485] tveeprom 1-0050: TV standards ATSC/DVB Digital (eeprom 0x80)
[   30.951487] tveeprom 1-0050: audio processor is None (idx 0)
[   30.951490] tveeprom 1-0050: decoder processor is CX882 (idx 25)
[   30.951492] tveeprom 1-0050: has no radio, has IR receiver, has no IR transmitter
[   30.951494] cx88[0]: hauppauge eeprom: model=90003
[   30.951564] input: cx88 IR (Hauppauge Nova-T DVB-T as /class/input/input5
[   30.951594] cx88[0]/2: cx2388x 8802 Driver Manager
[   30.951981] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 18
[   30.951991] ACPI: PCI Interrupt 0000:01:07.2[A] -> Link [LNKB] -> GSI 18 (level, low) -> IRQ 18
[   30.951999] cx88[0]/2: found at 0000:01:07.2, rev: 5, irq: 18, latency: 64, mmio: 0xdd000000
[   30.952177] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [LNKB] -> GSI 18 (level, low) -> IRQ 18
[   30.952186] cx88[0]/0: found at 0000:01:07.0, rev: 5, irq: 18, latency: 64, mmio: 0xde000000
[   30.952243] cx88[0]/0: registered device video1 [v4l2]
[   30.952270] cx88[0]/0: registered device vbi1
[   30.953219] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
[   30.953225] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LAZA] -> GSI 20 (level, low) -> IRQ 20
[   30.953796] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   30.961973] cx2388x dvb driver version 0.0.6 loaded
[   30.961977] cx8802_register_driver() ->registering driver type=dvb access=shared
[   30.961981] CORE cx88[0]: subsystem: 0070:9002, board: Hauppauge Nova-T DVB-T [card=18]
[   30.961984] cx88[0]/2: cx2388x based dvb card(some typos corrected)
[   30.991807] DVB: registering new adapter (cx88[0]).
[   30.991814] DVB: registering frontend 0 (Conexant CX22702 DVB-T)...
[   31.172999] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   31.972883] lp0: using parport0 (interrupt-driven).

```

And just in case anyone wonders - i have got the firmware dvb-fe-tda10046.fw in /lib/firmware.
Running Gutsy 7.10 2.6.22-14-generic on amd x64

---

