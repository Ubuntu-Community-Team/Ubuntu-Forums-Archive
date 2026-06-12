---
title: "System crash when running MythTV"
date: 2011-05-24
forum: Mythbuntu
---

### Post by mric5180 on 2011-05-24
Hi, 

I have a system setup as a mythTV backend + frontend on Ubuntu 11.04. I have the system set-up to shutdown automatically using Mythwelcome and start-up again via ACPI.

Often when the machine boots as a result of ACPI the system crashes shortly after boot. When i say crashes the screen does not change (i.e. it stays at whatever it was at the time of the crash), the system does not respond to mouse and keyboard, ping and SSH do not respond, the only way out is to press the power button. The other annoying thing is that it doesn't happen all the time, maybe 1 in 5.

I suspect the kernel or a driver in the kernel is crashing, perhaps it's related to ACPI or my tuner card drive, i really don't know. But i have no idea how to go about debugging this, so any helpful ideas as to logs to look at or other threads to read would be useful.

Other info that might be important is that I have two Tuner cards:
Leadtek DTV1000T
Leadtek DTV2000DS

Thanks in advance for any help.

SOLVED: adding "HPET=disable" to kernel boot in grub fixes issue.

---

