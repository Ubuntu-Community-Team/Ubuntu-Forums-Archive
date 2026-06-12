---
title: "No more ethernet network with pcmcia"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by vince21 on 2006-06-03
Hi all!

I have upgraded on Tuesday to Dapper Drake and since then the ethernet networking does not work.

*Machine:*
Laptop Toshiba Satellite 1100 without internal ethernet reaching Internet through a PCMCIA-Card

> - what chipset / adapter you're using
MicroNet PCMCIA Ethernet + Data/Fax Modem

#cardctl ident
Socket 1:
  product info: "PCMCIAs", "Fast Ethernet+56K ComboCard"
  manfid: 0x0143, 0xc0ab
  function: 0 (multifunction)
(It is a NE2000-compatible ethernet card)

> - what symptoms you experienced
The card is recognized the modem part is corretly initialized but the initialization of the Ethernet part of the pcmcia card fails.

Here is an extract from the /var/log/kernel
> [4294687.273000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[4294687.273000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[4294687.273000] cs: IO port probe 0x3000-0x3fff: clean.
[4294687.274000] pcmcia: parent PCI bridge Memory window: 0x34000000 - 0x38ffffff
[4294687.274000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[4294688.225000] pccard: PCMCIA card inserted into slot 1
[4294688.225000] cs: memory probe 0x34000000-0x38ffffff: excluding 0x34000000-0x380fffff
[4294688.232000] pcmcia: registering new device pcmcia1.0
[4294688.336000] cs: IO port probe 0x100-0x4ff: excluding 0x200-0x20f 0x4d0-0x4d7
[4294688.338000] cs: IO port probe 0xc00-0xcf7: clean.
[4294688.339000] cs: IO port probe 0xa00-0xaff: clean.
[4294688.348000] cs: IO port probe 0x100-0x4ff: excluding 0x200-0x20f 0x4d0-0x4d7
[4294688.350000] cs: IO port probe 0xc00-0xcf7: clean.
[4294688.351000] cs: IO port probe 0xa00-0xaff: clean.
[4294688.430000] pcmcia: registering new device pcmcia1.1
[4294688.484000] eth%d: pcnet_reset_8390() did not complete.
[4294688.494000] pcnet_cs: unable to read hardware net address for io base 0x3300
[4294688.635000] 1.1: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A


> - any workarounds you've tried and whether or not they worked?
I have tried the Workaround of
[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)
It doesnot work.

I have search Internet with Google and different Ubuntu forums and Wikis and it seems that the problem comes from Kernel-log line:
"pcnet_cs: unable to read hardware net address for io base 0x3300"

Here is the end of the output of
#lspci -v
> 0000:02:04.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 10
        Memory at 38000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 30000000-31fff000 (prefetchable)
        Memory window 1: 34000000-35fff000
        I/O window 0: 00003000-000030ff
        I/O window 1: 00003400-000034ff
        16-bit legacy interface ports at 0001

0000:02:04.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 10
        Memory at 38001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 32000000-33fff000 (prefetchable)
        Memory window 1: 36000000-37fff000
        I/O window 0: 00003800-000038ff
        I/O window 1: 00003c00-00003cff
        16-bit legacy interface ports at 0001

The address 0x3300 is outside of the IO-windows of the cardbridge.
But how can I change or correct this address?
Is it something to do in /etc/pcmcia/config.opts?
From my researches on Internet usually the address is 0x3000, which would fit in the allowed IO-window.

> - is this a regression for something that worked in previous versions of Ubuntu?
Yes. With Breezy everything was OK with ethernet networking with the Kernet 2.6.8

> - are you using DHCP?
No.

Thank you a lot for any help or idea

Vince

---

### Post by vince21 on 2006-06-04
Nobody knows how to configure a PCMCIA card?

It seems to me that it is a problem with the kernel of Dapper (2.6.15). With Breezy I had a 2.6.8 and everything worked fine.
I used Linux since 1998 and after some difficulties at the begining with the pcmcia card everything was OK for many years :D . I have tried another distro with the 2.6.15 Kernel (ArchLinux) and I have the same symptoms and problems :-k .

Many thank for your help!

Vince

---

### Post by kiolb on 2006-07-15
This seems to be a general networking problem with kernel 2.6.15-23. For I am using an Ethernet card with driver Davicom 21x4x DEC, which worked fine in Breezy and now with kernel 2.6.12-9. Only after an upgrade the problem started.:neutral:

---

### Post by kiolb on 2006-07-17
I did an update to kernel 2.6.15-26, which solved the problem.:cool:

---

