---
title: "How to mount a mixed data and audio CD correctly in Ubuntu"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by darkmaster on 2007-02-15
Hi everyone. I'm trying to correctly read with Ubuntu a Dreamcast backup game wich is a mixed data and audio one. I don't exactly know how it is done but when I insert it in Windows, it shows me a lot of data while if I insert it in Ubuntu it reads it as a music cd only! That's not correct. How do I mount it correctly?

We're talking about a Disk Juggler .cdi masterized disk format, a backup game for dreamcast. Chankast, the dreamcast emulator, works fine under wine, very quick too, but the fact that Ubuntu reads my CD as a sound only disc, makes wine read it the same way too (Wine just reads what's mounted in /media/cdrom0).

There's another way you can help me too. The other way is: how do I mount a .cdi disc image in wine? Anibody managed to have wine run alcohool 120% or daemon tools?

I've tested another Dreamcast emulator, the name's Demul. This emulator can run iso images too (And cdi, nrg, ecc...) and it works under Crossover. Having it to read a .cdi game, the emulator worked fine but both under windows and linux it is unplayable, too slow.

So, how can I mount correctly a mixed CD like this in Ubuntu? Any help will be very apprieciated!

P.S.: I tryed also

mount -t iso9660 -o ro /dev/cdrm /media/cdrom0

and the folder contained all the data indeed but the CD is still recognised as an audio cd by chankast.

---

