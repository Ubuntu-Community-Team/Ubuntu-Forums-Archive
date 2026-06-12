---
title: "soundcard Delta 1010LT not initialized"
date: 2010-10-14
forum: Multimedia Software
---

### Post by D.Artanidi on 2010-10-14
Hello there,
I'm not too experienced on Ubuntu, but I'm trying to get a Delta 1010LT working on Ubuntu 10.04 minimal install (no gnome, only console)> .

I can see the board detected using lspci, but looking at dmesg output I get the following:

```

[   31.116668] ICE1712 0000:05:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   31.116709] ice1712: Using board model M Audio Delta 1010LT
[   31.135560] invalid CS8427 signature 0x0: let me try again...
[   31.136074] unable to find CS8427 signature (expected 0x71, read 0x0),
[   31.136453]    initialization is not completed
[   31.136699] CS8427 initialization failed
[   31.136948] ICE1712 0000:05:00.0: PCI INT A disabled
[   31.136963] ICE1712: probe of 0000:05:00.0 failed with error -14

```

I tried to edit alsa-base .conf by entering: options snd-ice1712 model=delta1010lt
but the problem persists.

Please note if a change the model to delta1010 the driver is loaded correctly, but I assume there are major differences between the two boards so I don't get audio out, even if I unmute everything using alsamixer.

Motherboard is an Intel D510MO with onboard audio disabled.

Any advice on the issue?

Many thanks for your help.

Davide

---

### Post by D.Artanidi on 2010-10-19
bump

---

