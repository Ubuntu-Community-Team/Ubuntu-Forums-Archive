---
title: "Virmidi and USB midi cable"
date: 2010-10-13
forum: Multimedia Software
---

### Post by grackleman on 2010-10-13
Hi 
I'm using Ubuntu Lucid, an jOrgan, a USB midi interface and virmidi. The organ runs when the computer boots and has to have the keyboard input specified.

The problem is the random ordering of the USB midi interface and virmidi.
Half the time I get:

~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf7ff4000 irq 16
 1 [Cable          ]: USB-Audio - USB Midi Cable
                      USB Midi Cable at usb-0000:00:12.1-1, full speed
 2 [VirMIDI        ]: VirMIDI - VirMIDI
                      Virtual MIDI Card 1
and the other times '1' is virmidi and '2' is USB audio.

Is there a way of configuring it so that the order is always consistent?

Thanks
Peter

---

