---
title: "Slow Blender and freezes"
date: 2010-09-23
forum: Multimedia Software
---

### Post by andreselsuave on 2010-09-23
Hello,

I have this problem: I'm running blender (a 3d modeling program) in my machine and sometimes the computer slows down and after a while, the desktop logs out. My cpu and gpu are:
CPU:	Intel(R) Core(TM)2 Duo CPU E7400 @ 2.80GHz
GPU:	Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

I think it might be a graphic driver issue, or that my computer's video card is not too good. are there any propietary drivers for intel integrated video cards? 

my lshw -c video output:
```
 *-display:0             
       description: VGA compatible controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:34 memory:fe800000-febfffff memory:d0000000-dfffffff(prefetchable) ioport:ec90(size=8)

```

---

### Post by Ghost|BTFH on 2010-09-23
Your problem can be summed up right here:

> GPU: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

Basically, what you're trying to do right now is similar to jumping 30 buses with a moped.  It's not going to end pretty and there will be blood.

Get yourself a real video card (read as nVidia or ATi) and install the proper drivers for it.  This should resolve all your issues.

Cheers,
Ghost|BTFH

---

### Post by andreselsuave on 2010-09-23
Thanks a lot :)

Yeah, I imagined that videocard was not too good. Do you have any recommendations on a videocard for working with blender?

thanks :)

---

### Post by Ghost|BTFH on 2010-09-23
Basically, you want something with a strong GPU and a nice chunk of VRAM.  So, you want to look at the number crunching capabilities of the cards out there and comparison shop.

ATi has some better drivers than they've had in the past, and I've heard very good things about the GPUs of recent.  nVidia is still a staple for a lot of gamers (in fact, it's generally a 50/50 split between the two companies) but when it comes down to serious number crunching, I've heard noise that ATi out performs nVidia usually.

All that being said, those results are generally in Windows environments and currently the software for nVidia in Linux is superior to ATi's open-source version, which means the nVidia drivers will actually utilize the full capacity of the card where ATi's drivers will not.  

So, for casual use, and even for 3D gaming, ATi would be fine - for serious 3D number crunching however, I'd still currently go with nVidia.  If their drivers ever improve, ATi will however, squish nVidia.

As for a brand name, eVGA has been doing pretty well for me for the most part, I just make sure to get one that has a built-in fan and a comfortable chunk of VRAM.  Try to avoid the "silent cooling" features being touted by many companies, those can pretty much be summed up as "disposable 2 year video cards" and not much else.

---

### Post by andreselsuave on 2010-09-24
Thank you very much for the advice :) !
I'll see what I can get from my boss :D

---

