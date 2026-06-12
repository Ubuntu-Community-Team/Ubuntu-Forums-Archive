---
title: "AverMedia Hybrid Cardbus PCMCIA"
date: 2008-08-22
forum: Multimedia Software
---

### Post by juanan_ab on 2008-08-22
Hello, I can't install an AverMedia TV/DVB FM Hybrid CardBus PCMCIA in Ubuntu Hardy 64, dmesg:

[   34.322470] pccard: CardBus card inserted into slot 0
[   34.478075] saa7130/34: v4l2 driver version 0.2.14 loaded
[   34.478136] PCI: Enabling device 0000:0b:00.0 (0000 -> 0002)
[   34.478147] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.478156] saa7133[0]: found at 0000:0b:00.0, rev: 209, irq: 16, latency: 0, mmio: 0x6c000000
[   34.478166] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[   34.478171] saa7133[0]: subsystem: 1461:f436, board: AVerMedia TV Hybrid A16AR [card=99,insmod option]
[   34.478179] saa7133[0]: board init: gpio is 220000
[   34.478271] input: saa7134 IR (AVerMedia TV Hybrid as /devices/pci0000:00/0000:00:1e.0/0000:0a:03.0/0000:0b:00.0/input/input11
[   34.657928] saa7133[0]: i2c eeprom 00: 61 14 36 f4 00 00 00 00 00 00 00 00 00 00 00 00
[   34.657942] saa7133[0]: i2c eeprom 10: 00 ff e2 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[   34.657955] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 01 03 08 ff 00 ff ff ff ff ff
[   34.657966] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   34.657978] saa7133[0]: i2c eeprom 40: ff 65 00 ff c2 1e ff ff ff ff ff ff ff ff ff ff
[   34.657990] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   34.658001] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   34.658013] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   34.709055] saa7133[0]: registered device video0 [v4l2]
[   34.709080] saa7133[0]: registered device vbi0
[   34.709102] saa7133[0]: registered device radio0
[U][B][   34.807072] mt352_read_register: readreg error (reg=127, ret==-5)
[   34.807097] saa7133[0]/dvb: frontend initialization failed[/B][/U]
[   34.820817] saa7134 ALSA driver for DMA sound loaded
[   34.820846] saa7133[0]/alsa: saa7133[0] at 0x6c000000 irq 16 registered as card -2

lspci -v 

0b:00.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
	Subsystem: Avermedia Technologies Inc Unknown device f436
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at 6c000000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [40] Power Management version 2

modprobe saa7134 -> OK
modprobe saa7134-DVB -> OK
modprobe saa7134-alsa -> OK
modprobe mt352 -> OK

in /etc/modprobe.d/saa7134
options saa7134 card=99 alsa=1 tuner=67
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-dvb ; /sbin/modprobe tuner ; /sbin/modprobe mt352

tvtime -> No signal 
Me-TV -> No input device found
Xine->DVB-> Sorry, No DVB input device found. 
Kaffeine -> There's not DVB 

I've installed DVB-utils, My card is PCMCIA, my notebook: Sony Vaio VGN-FE41E running Ubuntu 8.04.1 64 bits, the card is detected AVerMedia TV Hybrid A16AR

Any suggestion?, Anybody could help me?, thanks!!!.

---

