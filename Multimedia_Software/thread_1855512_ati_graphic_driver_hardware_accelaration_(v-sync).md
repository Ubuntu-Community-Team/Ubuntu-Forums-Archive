---
title: "ati graphic driver hardware accelaration (v-sync)???"
date: 2011-10-06
forum: Multimedia Software
---

### Post by daniel227 on 2011-10-06
hello everybody,
i just changed from windows to ubuntu (11.04).
on my old (around 2005) laptop with this graphic card: Radeon RV250 [Mobility FireGL 9000]
it's  working fine but when watching movies i have this horizontal sharp  break going through the picture when the camera pans (i forget the name;  v-sync corrects it afaik).
i remember it was possible to fix this  under windows although it took some work with finding and installing ati  drivers (finding, mostly).

i'd like to fix this.
first of all i'd like to find out which driver linux is using and is hardware accelaration working partly or what.

i stumbled over some things while searching the forum (mesa-utils not installed, fglrx driver,...)
but i don't want to just blindly install things i don't have a clue about... any help?

oh, btw, system -> admin -> additional drivers - it's empty and doesn't offer any actions. it's just empty.

PS: i tried this: [FONT=Lucida Console]dmesg | grep drm[/FONT] (found it in a post)

and it returned this:

[FONT=Lucida Console][   24.867921] [drm] Initialized drm 1.1.0 20060810
[   25.422404] [drm] radeon defaulting to kernel modesetting.
[   25.422412] [drm] radeon kernel modesetting enabled.
[   25.427573] [drm] initializing kernel modesetting (RV250 0x1002:0x4C66).
[   25.427632] [drm] register mmio base: 0x90400000
[   25.427635] [drm] register mmio size: 65536
[   25.428924] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   25.428927] [drm] Driver supports precise vblank timestamp query.
[   25.428947] [drm] radeon: irq initialized.
[   25.429720] [drm] Detected VRAM RAM=128M, BAR=128M
[   25.429725] [drm] RAM width 64bits DDR
[   25.430120] [drm] radeon: 32M of VRAM memory ready
[   25.430125] [drm] radeon: 256M of GTT memory ready.
[   25.432936] [drm] Loading R200 Microcode
[   25.437203] [drm] radeon: ring at 0x00000000B0001000
[   25.437229] [drm] ring test succeeded in 1 usecs
[   25.437534] [drm] radeon: ib pool ready.
[   25.437655] [drm] ib test succeeded in 0 usecs
[   25.444276] [drm] Panel ID String: HTC                     
[   25.444282] [drm] Panel Size 1280x800
[   25.444744] [drm] Radeon Display Connectors
[   25.444748] [drm] Connector 0:
[   25.444751] [drm]   VGA
[   25.444755] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   25.444758] [drm]   Encoders:
[   25.444761] [drm]     CRT1: INTERNAL_DAC1
[   25.444764] [drm] Connector 1:
[   25.444767] [drm]   LVDS
[   25.444770] [drm]   DDC: 0x6c 0x6c 0x6c 0x6c 0x6c 0x6c 0x6c 0x6c
[   25.444773] [drm]   Encoders:
[   25.444776] [drm]     LCD1: INTERNAL_LVDS
[   25.444779] [drm] Connector 2:
[   25.444781] [drm]   S-video
[   25.444783] [drm]   Encoders:
[   25.444786] [drm]     TV1: INTERNAL_DAC2
[   25.689535] [drm] fb mappable at 0x98040000
[   25.689541] [drm] vram apper at 0x98000000
[   25.689544] [drm] size 1024000
[   25.689546] [drm] fb depth is 8
[   25.689549] [drm]    pitch is 1280
[   25.689905] fbcon: radeondrmfb (fb0) is primary device
[   25.691370] fb0: radeondrmfb frame buffer device
[   25.691373] drm: registered panic notifier
[   25.691388] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:00.0 on minor 0
[/FONT]
thanks for reading.

---

### Post by collisionystm on 2011-10-06
Just install the Catalyst driver for linux. 

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

---

### Post by daniel227 on 2011-10-07
thanks!
 a little explanation wouldn't have been lost on me.
anyhow, the download ends on .run and it seems linux can't deal with it.
would it happen to be the same as the catalyst center fglrx-amdcccle from ubuntu software center?

---

### Post by collisionystm on 2011-10-07
> **daniel227 said:**
> thanks!
 a little explanation wouldn't have been lost on me.
anyhow, the download ends on .run and it seems linux can't deal with it.
would it happen to be the same as the catalyst center fglrx-amdcccle from ubuntu software center?

Open a terminal

cd Downloads ( or wherever the file is)

sudo bash

chmod +x ati-driver-installer-11-9-x86.x86_64.run

./ati-driver-installer-11-9-x86.x86_64.run

Once it is installed, read the directions about running the ati config. Once you do that, just reboot!

---

### Post by daniel227 on 2011-10-10
first of all, thanks to collisionistm for taking some time for my troubles.
and now:
bloody ******* hell, i ****** up my system!!!

> Open a terminal

cd Downloads ( or wherever the file is)

sudo bash

chmod +x ati-driver-installer-11-9-x86.x86_64.run

./ati-driver-installer-11-9-x86.x86_64.run

Once it is installed, read the directions about running the ati config. Once you do that, just reboot! 	

- that didn't work because of permissions.
so i tried a step-by-step thingy [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually)
after which aticonfig just kept on returning "no suitable device found" or some such, after which my computer just wouldn't start up anymore after which i reinstalled ubuntu, and now it's working better than before (no tearing anymore)
:KS:KS:KS
the only thing's different now: -
- instead of vlc i installed mplayer (noGUI)
- before i had two partitions on my hard-drive, one for windoze (cool! a couple of weeks with linux and i'm qualified to use these derogative terms!) and one for linux, now it's just one, no need for grub anymore.

PS: i had just exactly the same kind of troubles with my ati graphic card and reinstalling windows so in my opinion it's not ati+ubuntu, but ati in general. hallelujah.

---

### Post by daniel227 on 2011-10-10
PPS: i did check that the tearing was not caused by a particular media player, it was the same on all.

---

