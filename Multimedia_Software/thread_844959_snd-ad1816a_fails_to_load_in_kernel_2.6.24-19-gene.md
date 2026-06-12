---
title: "snd-ad1816a fails to load in kernel 2.6.24-19-generic"
date: 2008-06-30
forum: Multimedia Software
---

### Post by Moulton on 2008-06-30
After upgrading to Hardy Heron, the module for my sound card, snd-ad1816a.ko, fails to load with this kernel error message:

> ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/isa/ad1816a/../../alsa-kernel/isa/ad1816a/ad1816a_lib.c:607: **ad1816a: can't grab DMA1 1**
ad1816a 01:01.00: **disabled**
**no AD1816A based soundcards found.**

If I drop back to my next older kernel, 2.6.22-15-generic, the sound card driver loads correctly and works normally.

Any suggestions?

---

### Post by xc3RnbFO8P on 2008-06-30
In /etc/modules see if there is a difference between
old and new kernel.

---

### Post by Moulton on 2008-06-30
> **Ringi said:**
> In /etc/modules see if there is a difference between
old and new kernel.

/etc/modules hasn't changed.

```

$ ls -l /etc/modules
-rw-r--r-- 1 root root 215 2007-08-15 19:51 /etc/modules

$ cat /etc/modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
snd-ad1816a
lp
```

---

### Post by Moulton on 2008-07-02
Here is more information on the parameters defined within the older and newer versions of the snd-1816a.ko module...

```

$ modinfo -k [COLOR="Red"]2.6.22-15-generic[/COLOR] snd-ad1816a

filename:       /lib/modules/2.6.22-15-generic/kernel/sound/isa/ad1816a/snd-ad1816a.ko
license:        GPL
description:    AD1816A, AD1815
author:         Massimo Piccioni <dafastidio@libero.it>
srcversion:     8B15513A45571F7B8C108F7
alias:          pnp:cTER1411dADS7180dADS7181*
alias:          pnp:cTER1112dADS7180dADS7181*
alias:          pnp:cSMM7180dADS7180dADS7181*
alias:          pnp:cMDK1605dADS7180dADS7181*
alias:          pnp:cLWC1061dADS7180dADS7181*
alias:          pnp:cAZT1022dAZT1018dAZT2002*
alias:          pnp:cADS7181dADS7180dADS7181*
alias:          pnp:cADS7180dADS7180dADS7181*
alias:          pnp:cADS7150dADS7150dADS7151*
depends:        snd,snd-opl3-lib,snd-pcm,snd-mpu401-uart,snd-timer
vermagic:       2.6.22-15-generic SMP mod_unload 586 
parm:           index:Index value for ad1816a based soundcard. (array of int)
parm:           id:ID string for ad1816a based soundcard. (array of charp)
parm:           enable:Enable ad1816a based soundcard. (array of bool)
[COLOR="Red"]parm[/COLOR]:           port:Port # for ad1816a driver. (array of long)
[COLOR="Red"]parm[/COLOR]:           mpu_port:MPU-401 port # for ad1816a driver. (array of long)
[COLOR="Red"]parm[/COLOR]:           fm_port:FM port # for ad1816a driver. (array of long)
[COLOR="Red"]parm[/COLOR]:           irq:IRQ # for ad1816a driver. (array of int)
[COLOR="Red"]parm[/COLOR]:           mpu_irq:MPU-401 IRQ # for ad1816a driver. (array of int)
[COLOR="Red"]parm[/COLOR]:           dma1:1st DMA # for ad1816a driver. (array of int)
[COLOR="Red"]parm[/COLOR]:           dma2:2nd DMA # for ad1816a driver. (array of int)
parm:           clockfreq:Clock frequency for ad1816a driver (default = 0). (array of int)

```

```

$ modinfo -k [COLOR="Red"]2.6.24-19-generic[/COLOR] snd-ad1816a

filename:       /lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/isa/ad1816a/snd-ad1816a.ko
license:        GPL
description:    AD1816A, AD1815
author:         Massimo Piccioni <dafastidio@libero.it>
srcversion:     491978F9089005816137AA2
alias:          pnp:cTER1411dADS7180dADS7181*
alias:          pnp:cTER1112dADS7180dADS7181*
alias:          pnp:cSMM7180dADS7180dADS7181*
alias:          pnp:cMDK1605dADS7180dADS7181*
alias:          pnp:cLWC1061dADS7180dADS7181*
alias:          pnp:cAZT1022dAZT1018dAZT2002*
alias:          pnp:cADS7181dADS7180dADS7181*
alias:          pnp:cADS7180dADS7180dADS7181*
alias:          pnp:cADS7150dADS7150dADS7151*
depends:        snd,snd-opl3-lib,snd-pcm,snd-mpu401-uart,snd-timer
vermagic:       2.6.24-19-generic SMP mod_unload 586 
parm:           index:Index value for ad1816a based soundcard. (array of int)
parm:           id:ID string for ad1816a based soundcard. (array of charp)
parm:           enable:Enable ad1816a based soundcard. (array of bool)
parm:           clockfreq:Clock frequency for ad1816a driver (default = 0). (array of int)

```

The newer version of snd-ad1816a.ko, as used in the default kernel for Hardy Heron, [COLOR="Red"]omits the parameter variables[/COLOR] that are needed to properly address the sound card.  

Given this clue, is there a sensible way to proceed to solve the problem?

---

### Post by xc3RnbFO8P on 2008-07-02
I think you should report a bug.
Send this latest information.

---

### Post by Moulton on 2008-07-03
I've started by E-Mailing the module's author with the contents of this thread.  If I don't hear back from him within a week, I'll research the process for filing a bug report.

The AD1816 is the native audio on the mother board of my oldish HP Kayak.  My alternative is to plug in a newer PCI sound card, for which there is better driver support in ALSA Base.

---

### Post by luc0zade on 2009-01-06
Hi, has there been any progress on this?

I am also having problems with a sound card in a HP Kayak desktop running 8.04.1 Hardy, kernel 2.6.24.  The soundcard is an AZT1008 which uses the snd-azt2320 module, also authored by Massimo Piccioni.  I am seeing a similar error in dmesg - **can't grab DMA1 1** - and also missing parameter variables when I use modinfo to compare the driver in the 2.6.24 kernel with the older 2.6.22 kernel.

The problem with snd-azt2320 has already been recorded as [bug #237958 on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/237958").

---

### Post by Moulton on 2009-07-06
This issue appears to be fixed in the current kernel for Jaunty.  It still doesn't work in Hardy.

Since I now have another PCI sound card installed, I can now successfully load the snd-ad1816a.ko module provided I include a parameter option (in my case index=2) to indicate which sound card index slot to use for the AD1816a.

In /etc/modules, I put:  snd-ad1816a index=2

---

