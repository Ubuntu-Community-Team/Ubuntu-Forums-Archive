---
title: "No ICE1712 cards found - M-Audio sound card."
date: 2009-11-01
forum: Multimedia Software
---

### Post by dchurch24 on 2009-11-01
Hi all,

I've just installed UbuntuStudio 64 bit (real time kernel), and everything is fine (well, getting there).

The only thing I haven't been able to (slowly) fix is my soundcard.

It's listed in 'lspci':

```

03:00.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

```

 modinfo snd-ice1724 gives me:
```

filename:       /lib/modules/2.6.31-9-rt/kernel/sound/pci/ice1712/snd-ice1724.ko
license:        GPL
description:    VIA ICEnsemble ICE1724/1720 (Envy24HT/PT)
author:         Jaroslav Kysela <perex@perex.cz>
srcversion:     0F97D93286EF5C787D1DE33
alias:          pci:v00001412d00001724sv*sd*bc*sc*i*
depends:        snd,snd-ac97-codec,snd-pcm,snd-i2c,snd-ice17xx-ak4xxx,snd-rawmidi,snd-pt2258,snd-ak4xxx-adda,snd-ak4114
vermagic:       2.6.31-9-rt SMP preempt mod_unload modversions 
parm:           index:Index value for ICE1724 soundcard. (array of int)
parm:           id:ID string for ICE1724 soundcard. (array of charp)
parm:           enable:Enable ICE1724 soundcard. (array of bool)
parm:           model:Use the given board model. (array of charp)

```

...so I think I've loaded the module ok.

However, dmesg |grep ICE returns:

```

[   19.091552] ICE1712 0000:03:00.0: PCI INT A -> Link[LNEC] -> GSI 17 (level, low) -> IRQ 17
[   19.114245] ICE1712 0000:03:00.0: PCI INT A disabled
[   19.115304] ICE1712: probe of 0000:03:00.0 failed with error -14

```

So I have no idea what I'm doing wrong.

If I try to run envy24control I simply get:

```

No ICE1712 cards found

```

I have a dual boot (well, in fact another HDD) with 8.04 - everything works fine in there, so I know the hardware is good.

---

### Post by Yellow Pasque on 2009-11-01
Shouldn't the module loaded be snd-ice1712.ko? [http://www.alsa-project.org/main/index.php/Matrix:Module-ice1712](http://www.alsa-project.org/main/index.php/Matrix:Module-ice1712)

---

### Post by dchurch24 on 2009-11-01
Yes, quite right. I've since changed that, but I still get the same error:

 modinfo snd-ice1712
filename:       /lib/modules/2.6.31-9-rt/kernel/sound/pci/ice1712/snd-ice1712.ko
license:        GPL
description:    ICEnsemble ICE1712 (Envy24)
author:         Jaroslav Kysela <perex@perex.cz>
srcversion:     0B183929429B4C5102B7D09
alias:          pci:v00001412d00001712sv*sd*bc*sc*i*
depends:        snd-pcm,snd,snd-i2c,snd-mpu401-uart,snd-ice17xx-ak4xxx,snd-cs8427,snd-ak4xxx-adda,snd-ac97-codec
vermagic:       2.6.31-9-rt SMP preempt mod_unload modversions 
parm:           index:Index value for ICE1712 soundcard. (array of int)
parm:           id:ID string for ICE1712 soundcard. (array of charp)
parm:           enable:Enable ICE1712 soundcard. (array of bool)
parm:           omni:Enable Midiman M-Audio Delta Omni I/O support. (array of bool)
parm:           cs8427_timeout:Define reset timeout for cs8427 chip in msec resolution. (array of int)
parm:           model:Use the given board model. (array of charp)
parm:           dxr_enable:Enable DXR support for Terratec DMX6FIRE. (array of int)

---

### Post by Yellow Pasque on 2009-11-01
Hmm, maybe this will help: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3327](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3327)

---

### Post by dchurch24 on 2009-11-01
Ha ha !

You Sir, are a diamond!

I didn't find that page when googling (but then I wasn't a signed up member I suppose).

The answer was amoungst the bug chat:

I had to add

options snd-ice1712 model=delta66    (or delta1010LT)

in the 

# Prevent abnormal drivers from grabbing index 0

section of /etc/modprobe.d/alsa-base.conf

Had to fiddle around a bit with Jack after that (I can't remember exactly what I did, but it was in the output settings).

Thank you very much indeed!

---

### Post by cryptozoon on 2012-11-28
can't get this page at  [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3327](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3327)
maybe another source, Please? I have same issue

---

### Post by CharlesA on 2012-11-28
This thread is three years old. It would be better to create a new thread.

---

### Post by sandyd on 2012-11-28
**necromancing - thread closed**
As per the ubuntu forums code of conduct, please do not post in threads over one year old

Thanks!

---

### Post by sandyd on 2012-11-28
> **sandyd said:**
> **necromancing - thread closed**
As per the ubuntu forums code of conduct, please do not post in threads over one year old

Thanks!

ninja-d by multi-mod.
double close = open :P

---

