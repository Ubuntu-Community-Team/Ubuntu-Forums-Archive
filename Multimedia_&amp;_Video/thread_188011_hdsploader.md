---
title: "hdsploader"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by voxish on 2006-06-03
Hi folks,
I'm trying to get my multiface card to work, but the hdsploader is missing a .bin file. There's a post about this on the Dapper forum but it's closed. Does anyone know where to find the file on the net?
Thanks alot

hdsploader - firmware loader for RME Hammerfall DSP cards
Looking for HDSP + Multiface or Digiface cards :
Card 0 : NVidia nForce3 with AD1981B at 0xe0002000, irq 201
Card 1 : RME Hammerfall DSP at 0xe0400000, irq 177
Upload firmware for card hw:1
Unable to open file '/usr/share/alsa/firmware/hdsploader/multiface_firmware_rev11.bin' for reading

---

### Post by 5tr4t4 on 2006-06-04
[QUOTE=voxish]Hi folks,
I'm trying to get my multiface card to work, but the hdsploader is missing a .bin file. There's a post about this on the Dapper forum but it's closed. Does anyone know where to find the file on the net?
Thanks alot

hdsploader - firmware loader for RME Hammerfall DSP cards
Looking for HDSP + Multiface or Digiface cards :
Card 0 : NVidia nForce3 with AD1981B at 0xe0002000, irq 201
Card 1 : RME Hammerfall DSP at 0xe0400000, irq 177
Upload firmware for card hw:1
Unable to open file '/usr/share/alsa/firmware/hdsploader/multiface_firmware_rev11.bin' for reading[/QUOTE]

That IRQ is odd...

The problem is, simply, missing "firmware".  There is "alsa-firware-loaders" including hdsploader but the firmware itself is not available except through:

1. Another debian repo (possible the Agnula guys have it...I know there was some Agnula controversy around including "non-free" "firmware")
2. Download the "alsa-firmware" sources from alsa-project.org and "./configure --prefix=/usr ; make ; make install" from scatch.

I did the latter and have my multiface up and running.

Cheers

---

### Post by voxish on 2006-06-08
got it!
Thanks so much

---

