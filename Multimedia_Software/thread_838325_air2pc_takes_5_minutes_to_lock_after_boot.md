---
title: "air2pc takes 5 minutes to lock after boot"
date: 2008-06-23
forum: Multimedia Software
---

### Post by allene222 on 2008-06-23
My new system with v 0.2 air2pc cards works fine but takes 5 minutes to lock after a boot.  I built a prototype on an old P4 computer with these cards and it booted up fine.

lspci -v gives me this:

03:06.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)
        Subsystem: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card
        Flags: bus master, slow devsel, latency 64, IRQ 18
        Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at e800 [size=32]

03:07.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)
        Subsystem: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at febe0000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at e400 [size=32]


and what I think might be a relevant part of /var/log/messages is (I replaced "messages:Jun 23 08:08:25 myth_desktop kernel: [   30.023748]" with "kernel:"):

 kernel:  b2c2-flexcop: found the bcm3510 at i2c address: 0x0f
 kernel:  DVB: registering frontend 0 (Broadcom BCM3510 VSB/QAM frontend)...
 kernel:  b2c2-flexcop: initialization of 'Air2PC/AirStar 2 ATSC 1st generation' at the 'PCI' bus controlled by a 'FlexCopIIb' complete
 kernel:  flexcop-pci: will use the HW PID filter.
 kernel:  flexcop-pci: card revision 2
 kernel:  ACPI: PCI Interrupt 0000:03:07.0[A] -> GSI 22 (level, low) -> IRQ 16
 kernel:  DVB: registering new adapter (FlexCop Digital TV device)
 kernel:  b2c2-flexcop: MAC address = 00:d0:d7:30:10:39
 kernel:  nxt200x: nxt200x_readbytes: i2c read error (addr 0x0a, err == -121)
 kernel:  Unknown/Unsupported NXT chip: 00 00 00 00 00
 kernel:  lgdt330x: i2c_read_demod_bytes: addr 0x59 select 0x02 error (ret == -121)
 kernel:  bcm3510: Revision: 0x1, Layer: 0xb.
 kernel:  b2c2-flexcop: found the bcm3510 at i2c address: 0x0f
 kernel:  DVB: registering frontend 1 (Broadcom BCM3510 VSB/QAM frontend)...
 kernel:  b2c2-flexcop: initialization of 'Air2PC/AirStar 2 ATSC 1st generation' at the 'PCI' bus controlled by a 'FlexCopIIb' complete


The only thing that looks odd is the ic2 read error.  I am not even sure that is part of this chip.  It seems to have initialized correctly in the end.

I have tried each board by itself and they act the same.  I have spent hours searching for a solution.  I found that others have had this problem in the past, but did not find solutions.  I have talked to people who do not have this problem so know it is some kind of bug.  All this hardware is new and returnable if I could figure out what the cause is for sure.  Everything else is working at this point.

MB is ASUS M3A
CPU is AMD 5400+
2G memory
Video is ASUS EN6200LE TC1G
SATA HD

I would like to keep this computer in standby when not recording or watching but waiting 5 minutes to watch TV seems like a lot to ask.

Help would be appreciated.

Allen

---

