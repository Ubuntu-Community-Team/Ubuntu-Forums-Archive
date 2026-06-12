---
title: "Firewire card broken?"
date: 2008-11-07
forum: Multimedia Software
---

### Post by jeays on 2008-11-07
I just bought a Firewire card, and cannot make it work with either dvgrab or kino, connected to a Sony PV-GS80 camcorder.

Does this output suggest a defective card?

napoleon 505 /var/log $ dmesg | grep 1394
[   32.255959] ohci1394: fw-host0: Unrecoverable error!
[   32.255969] ohci1394: fw-host0: Async Req Rcv Context died: ctrl[00008806] cmdptr[1f8de001]
[   32.255986] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[18]  MMIO=[e5000000-e50007ff]  Max Packet=[2]  IR/IT contexts=[4/8]
[   32.256986] ohci1394: fw-host0: Unrecoverable error!
[   32.256993] ohci1394: fw-host0: Async Req Rcv Context died: ctrl[00008806] cmdptr[1f8de001]
[   32.256999] ohci1394: fw-host0: Async Rsp Rcv Context died: ctrl[00008806] cmdptr[37f80001]
[   32.260992] ohci1394: fw-host0: Serial EEPROM has suspicious values, attempting to set max_packet_size to 512 bytes
[   33.573359] ohci1394: fw-host0: Unrecoverable error!
[   33.573372] ohci1394: fw-host0: Async Req Tx Context died: ctrl[00008806] cmdptr[1f8f2002]
[   33.573379] ohci1394: fw-host0: Async Req Rcv Context died: ctrl[00008806] cmdptr[1f8de001]
[   33.573386] ohci1394: fw-host0: Async Rsp Rcv Context died: ctrl[00008806] cmdptr[37f80001]
[   33.573568] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001106005350d195]
[   53.139462] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   59.853765] ieee1394: raw1394: /dev/raw1394 device initialized
[   59.878628] video1394: Installed video1394 module
[61308.632389] ohci1394: fw-host0: SelfID received outside of bus reset sequence
[61323.974345] ohci1394: fw-host0: SelfID received outside of bus reset sequence

---

### Post by cariboo on 2008-11-07
It looks like your tv tuner card is interfering with the firewire card, pull the tuner card just to see if the firewire card gets setup. If it does work you may have to do some irq adjustment in you BIOS.

Jim

---

### Post by jeays on 2008-11-07
Thanks very much - I will try that tomorrow, and report back.

---

### Post by jeays on 2008-11-09
No, removing the TV card didn't make any difference.  Thanks for the suggestion anyway.

---

