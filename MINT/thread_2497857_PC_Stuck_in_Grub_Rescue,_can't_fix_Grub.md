---
title: "PC Stuck in Grub Rescue, can't fix Grub"
date: 2024-05-21
forum: MINT
---

### Post by hkk506 on 2024-05-21
Hi,

I recently had my power supply fail taking with it the motherboard and cpu. I have reinstalled all of these retired components but when I go to load up my PC, I am stuck in grub rescue. Previously, I had both linux and windows on the PC.

I loaded a live copy of Linux mint using a USB and followed the instructions here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The pastebin associated with the attempt to fix grub is here: [https://paste.ubuntu.com/p/Hf2SfVxBNf/](https://paste.ubuntu.com/p/Hf2SfVxBNf/)
Attempting to fix grub did not change anything and I am still just stuck in grub rescue. 

Any ideas of how to fix this would be greatly appreciated.

---

### Post by tea for one on 2024-05-21
[COLOR="#0000FF"]Lines 14 > 18[/COLOR] - No OS to fix, repair file systems and backup data recommended.
This does not bode well.
Boot-repair cannot see Windows nor your Linux OS.
It appears that your disks/filesystems were also damaged following the failure of your power supply.

[COLOR="#0000FF"]Line 163 > 167[/COLOR] - No sign of ESP
Both systems in old-fashioned Legacy mode although your system is EFI compatible.
Which version of Windows and what is the other OS?

Do you have backups of your personal data?

---

### Post by hkk506 on 2024-05-21
Thanks for the response. 
What do you think is the best way to try repair the file systems and get at the personal data there?
I previously had Windows 10 and Linux mint installed.

Most has been backed up although I have some work on previous unfinished projects still on the old drives.

---

### Post by tea for one on 2024-05-21
It is recommended to use Windows tools (chkdsk) for Microsoft file systems.
For ext4, you can boot into a live "Try Ubuntu" session and use fsck.

Whether the repair is successful depends on the extent of any damage?

How did you end up with Windows 10 in Legacy mode?
Microsoft has been stipulating Windows installations in UEFI mode for more than 10 years?

---

### Post by hkk506 on 2024-05-21
I will give that a shot thanks. 

I'll be honest I am not sure, I installed windows 10 for free when it came out. 

Thanks for all your help.

---

### Post by ajgreeny on 2024-05-21
*Thread moved to **MINT**.* which is more appropriate and a better fit.

---

### Post by Rubi1200 on 2024-05-22
Note that the repair summary has already attempted an fsck on the partitions, although unsuccessfully.

I would boot with a live USB, choose to Try Ubuntu and then open a terminal and try the boot repair suggestions from lines 47 or 49:
```

e2fsck -b 8193 <device>
or
e2fsck -b 32768 <device>

```

> The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock


It's kind of a long shot but worth trying.

---

