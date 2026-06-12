---
title: "ENLTV Card - Driver Patch"
date: 2007-01-18
forum: Multimedia &amp; Video
---

### Post by smitj02 on 2007-01-18
Hello,

I am trying to configure a new TV Capture Card (Encore ENLTV) in my Edgy box.  The card installed fine and the correct driver is being loaded, but it doesn't detect my card.  

I found some posts using Google referring to a linux [patch]("http://lkml.org/lkml/2006/12/5/361") that appears to reference my exact card but I don't know how to download and install a driver patch.  I also found a message stating that the patch was "removed because it was merged into a mainline or subsystem tree".  Thinking that perhaps a newer kernel would include the updated driver, i ran an update in the package manger to install the kernel version 2.4.27-12 but that doesn't seem to have changed anything.  The saa7134 driver reports the following:

[17179948.060000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179948.064000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179948.064000] saa7130[0]: found at 0000:02:0b.0, rev: 1, irq: 11, latency: 66, mmio: 0x40300000
[17179948.064000] saa7130[0]: subsystem: 1131:2342, board: UNKNOWN/GENERIC [card=0,autodetected]
[17179948.064000] saa7130[0]: board init: gpio is 5d31ff
[17179948.216000] saa7130[0]: i2c eeprom 00: 31 11 42 23 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[17179948.216000] saa7130[0]: i2c eeprom 10: ff ff 00 00 31 30 4d 4f 4f 4e 53 37 31 33 30 20
[17179948.216000] saa7130[0]: i2c eeprom 20: 41 42 48 53 ff ff ff ff ff ff ff ff ff ff ff ff
[17179948.216000] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179948.216000] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179948.216000] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179948.216000] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179948.216000] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179948.264000] saa7130[0]: registered device video1 [v4l2]
[17179948.324000] saa7130[0]: registered device vbi1
[17179948.356000] saa7134 ALSA driver for DMA sound loaded
[17179948.360000] saa7130[0]/alsa: saa7130[0] at 0x40300000 irq 11 registered as card -1

Note that the subsystem 1131:2342 is in the patch file above, but here it comes up as UNKNOWN/GENERIC.

There is a previous post about a card very similar to mine an ENLTV-FM.  Someone replied to user card=3 tuner=2, I tried this but with no luck.  Mine is just an ENLTV card with no FM on the end.

So do the experts agree that what I need to do is install this patch?  If so how do I determine where to get it from?  Then how do I install it?  Alternatively how long should I expect to wait for this patch to just show up in Ubunutu?  Is there somewhere I can look to see where the patch is in the pipeline?

Sorry for the long message and Thanks for any help,

Jonathan Smith
smitj02 AT hotmail

---

### Post by smitj02 on 2007-01-19
Is there a better place to ask this question?

---

### Post by smitj02 on 2007-01-20
OK, this is my last attempt to get an answer.  Is this question too advanced or obscure?

---

### Post by Vox754 on 2007-02-03
Hold on buddy.

By your description it seems you only need to set correctly your card and tuner, and everything should work fine.
I'm sure there is an updated list like the following
[http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)

I would suggest
```

sudo modprobe saa7134 card=0 tuner=0

```

Also when you try to watch television, for instance with "vlc", you should use "/dev/video1" instead of "/dev/video0".

I have to say that these ENCORE ENLTV cards are obscure and cheap.
Next time I'll try to buy a big-name card, Hauppage or something like that.

Good luck.

---

