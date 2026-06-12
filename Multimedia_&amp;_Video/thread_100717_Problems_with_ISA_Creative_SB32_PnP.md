---
title: "Problems with ISA Creative SB32 PnP"
date: 2005-12-08
forum: Multimedia &amp; Video
---

### Post by henriqueqc on 2005-12-08
Hi! it's my first post here at ubuntuforums.org although I read it a lot! 
I'm having some trouble setting up my sound card. 
I have installed the isapnp package, and the result from **# dmesg | grep -i pnp**  is:
```
[4294672.776000] pnp: PnP ACPI init
[4294672.785000] pnp: PnP ACPI: found 13 devices
[4294672.785000] PnPBIOS: Disabled by ACPI PNP
[4294672.788000] pnp: 00:02: ioport range 0xe400-0xe47f could not be reserved
[4294672.788000] pnp: 00:02: ioport range 0xe800-0xe80f has been reserved
[4294672.788000] pnp: 00:02: ioport range 0x290-0x297 has been reserved
[4294672.790000] isapnp: Scanning for PnP cards...
[4294672.922000] pnp: SB audio device quirk - increasing port range
[4294672.922000] pnp: AWE32 quirk - adding two ports
[4294672.922000] isapnp: Card 'Creative SB32 PnP'
[4294672.922000] isapnp: 1 Plug & Play card detected total
[4294672.963000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294716.865000] pnp: Device 01:01.00 activated.
[4294716.865000] sb: PnP: Found Card Named = "Creative SB32 PnP", Card PnP id = CTL009C, Device PnP id = CTL0041
[4294716.865000] sb: PnP:      Detected at: io=0x220, irq=5, dma=1, dma16=5
[4294717.104000] parport: PnPBIOS parport detected.
[4294729.454000] pnp: Device 01:01.01 activated.
[4294729.482000] gameport: NS558 PnP Gameport is pnp01:01.01/gameport0, io 0x200, speed 693kHz
```

Then i did a **# pnpdump > /etc/isapnp.conf** and edited it. Here's the lines that i have uncommented.

```
(INT 0 (IRQ 5 (MODE +E)))
(DMA 0 (CHANNEL 1))
(DMA 1 (CHANNEL 5))
(IO 0 (SIZE 16) (BASE 0x0220))
(IO 1 (SIZE 2) (BASE 0x0330))
(IO 2 (SIZE 4) (BASE 0x0388))
(NAME "CTL009c/268720544[0]{Audio               }")
(ACT Y)
```

But when i run **# /etc/init.d/isapnp start** it says:

```
Board 1 has Identity dd 10 04 59 a0 9c 00 8c 0e:  CTL009c Serial No 268720544 [checksum dd]
/etc/isapnp.conf:47 -- Fatal - resource conflict allocating IRQ5 (see /proc/interrupts)
/etc/isapnp.conf:47 -- Fatal - Error occurred executing request 'IRQ 5' --- further action aborted
```

The strange thing is that from **# cat /proc/interrupts** i get:
```
  5:          2          XT-PIC  soundblaster
```

I did all that because just doing **# modprobe sb io=0x220, irq=5, dma=1, dma16=5** was not working even though the module was getting loaded.

Am i doing it all wrong? Please help me :) . Sorry about my English i'm from Brazil.

---

### Post by az on 2005-12-08
Since linux is not PNP since probing the isa bus can cause they system to freeze, you need to tell your hardware how to manage your card.

"resource conflict allocating IRQ5 "

Can you set your bios to reserve irq 5 for the isa bus?  Or something to the like.  It depends on your bios how to go about it.

---

