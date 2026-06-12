---
title: "nvidia driver 331.38 freezes at login"
date: 2014-05-29
forum: Multimedia Software
---

### Post by sidewalkcynic on 2014-05-29
I have access to the partitions via a different installation on the HDD.

How do I change the driver back to the Nouveau, or possibly, to the 331.38-updates, or 304.117 driver?

---

### Post by ajgreeny on 2014-05-29
> **sidewalkcynic said:**
> I have access to the partitions via a different installation on the HDD.

How do I change the driver back to the Nouveau, or possibly, to the 331.38-updates, or 304.117 driver?
No need to do it that way.
Just use Ctrl+Alt+F1 to get to a command line (assuming you can) and there you can remove the nvidia driver you have at the moment and then if you wish install nvidia-current with ```
sudo apt-get install nvidia-current
```
If Ctrl+Alt+F1 does not work and the whole machine is frozen you can boot to recovery mode from the grub menu and do the same thing from that.

---

