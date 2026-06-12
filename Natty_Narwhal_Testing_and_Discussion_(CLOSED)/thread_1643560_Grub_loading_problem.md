---
title: "Grub loading problem"
date: 2010-12-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by fil0~ on 2010-12-12
I've been experiencing this problem for some days now. Grub does not load at startup and I only get a flashing underscore; HD LED remains turned off.
To boot ubuntu I have to boot from live cd and then restart, in this way grub menu appears immediately.
I also noticed that, when the system is started, if I choose restart I have no problems, but if I turn off my laptop and then I restart the system I get the initial problem again.
May this problem be caused by the fact that I have a separate /boot partition (ext4) and a / with btrfs?

I have grub2 (1.99~20101126-1ubuntu3) natty.

Thanks in advance.

---

### Post by dino99 on 2010-12-13
why not a standard installation: ext3/ext4, /, /home, swap (only) ?

---

### Post by fil0~ on 2010-12-13
Because I wanted to try btrfs... and grub2 does not support it, so i need a /boot partition too.

May the problem be related to my BIOS?

---

### Post by cariboo on 2010-12-13
I had the same problem when I tried btrfs, I had to manually edit /boot/grub/grub.cfg adding the proper UUID for /boot. 

I have since gone back to ext4, as "Butter FS " was so glacially slow, I installed shortly after the toolchain was uploaded, and the upgrade from Maverick took close to 6 hours, all the packages downloaded in a reasonable amount of time, but all the disk writes were incredibly slow.

If it had been on a system I use all the time, I would have halted the upgrade right then and there, but it was on an extra system so I kept it for a week or so afterwards, even normal upgrades were taking 2 to 3 times longer than a system with ext4.

For me "Butter FS" isn't ready for prime time yet.

---

### Post by fil0~ on 2010-12-13
For the slowness of dpkg with btrfs I solved with this ppa [https://launchpad.net/~brian-rogers/+archive/btrfs](https://launchpad.net/~brian-rogers/+archive/btrfs) , with that version of the package manager the system is fast again.

Cariboo I think my problem is radically different because when I manage to get to menu of grub, after having restarted from the live cd, the kernel and the system load nominally, so I think my UUID are correct. Where I am wrong?

---

### Post by cariboo on 2010-12-13
File transfer where also very slow, it wasn't only dpkg.

It seems your problem may be something different, do you have an OEM version of Windows installed on the system too? If you do does this only happen after running Windows, or all the time?

---

### Post by fil0~ on 2010-12-13
I have also Windows, installed by myself, but are months that i don't use it! I would dare to exclude it could be cause of my flashing underscore on screen...
The problem happens at every start but not on reboot.

---

### Post by cariboo on 2010-12-13
> **fil0~ said:**
> I have also Windows, installed by myself, but are months that i don't use it! I would dare to exclude it could be cause of my flashing underscore on screen...
The problem happens at every start but not on reboot.

OK that isn't your problem then, the only reason I asked, is that some OEM restore utilities overwrite the mbr right where grub resides, which causes boot problems.

I haven't kept up with that particular bug, and it may have been solved by now.

---

### Post by fil0~ on 2010-12-22
This command solved my problem: ```
sudo dpkg-reconfigure grub-pc
```

---

