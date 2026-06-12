---
title: "Removing ATI Catalyst Control Driver"
date: 2013-02-25
forum: Multimedia Software
---

### Post by laserpainter2 on 2013-02-25
Hello all, I attempted to install ati catalyst driver and failed, right now my system boots fine but stuck in a low resolution, I would like to revert back to the default driver that came with lubuntu, I am running Lubuntu 12.10 AMD 64 with an ATI Radeon HD 4200 series. I did not make any backups of anything :(. Thanks in advance,

---

### Post by QIII on 2013-02-25
[I]Moved to [B]Mulitmedia & Video

[/B][/I]How did you install the driver?  That will dictate how it is removed.

Thanks.

---

### Post by laserpainter2 on 2013-02-25
I downloaded it via amds website, and installed it through the terminal.
It was a run file.

This is the file name it has on my desktop amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64, I am new to lubuntu and know when uninstalling software I use the command sudo apt-get remove <packagename> but I can't remove it that way.

---

### Post by laserpainter2 on 2013-02-25
> **laserpainter2 said:**
> I downloaded it via amds website, and installed it through the terminal.
It was a run file.

This is the file name it has on my desktop amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64, I am new to lubuntu and know when uninstalling software I use the command sudo apt-get remove <packagename> but I can't remove it that way.


Thanks for your help I seemed to fix the problem by issuing this command sudo apt-get rem--purge fglrx fglrx-amdcccle. the only problem left is I still seeing the ati catalyst control center in my start menu.

---

