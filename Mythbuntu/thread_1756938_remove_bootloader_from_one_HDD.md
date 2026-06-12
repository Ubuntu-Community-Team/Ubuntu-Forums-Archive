---
title: "remove bootloader from one HDD"
date: 2011-05-12
forum: Mythbuntu
---

### Post by davidstoll on 2011-05-12
I reinstalled mythbuntu and while I was going through the menus, I believe I accidentally installed the bootloader to the wrong HDD.

It's a secondary drive that I mount for recordings and other things.  Anyway, It boots fine if I disconnect that drive.  My bios has the boot order correct, but for some reason, it still wants to try the other disk first.

How can I remove the boot loader without loosing the data on the disk?  Or maybe there is something else I can do?

Right now, when I boot, it says that a particular UUID does not exist and drops me to a grub prompt.

Thank you for any help you can give.

---

### Post by this_costs_more_cell_bill on 2011-12-24
I have the same question!
I have 2 harddrives: one SATA 640GB (used just to store data) the other IDE (used to run the Ubuntu Linux).
I want the IDE one to boot, but even if I set it up to boot first from BIOS, the SATA one is always booting itself.

I want to erase the bootloader from the SATA one, but keep the data on it.

---

### Post by gordintoronto on 2011-12-24
You could try this: disconnect the secondary drive, boot Ubuntu, open a Terminal and enter this command:
sudo update-grub

No guarantee, of course.

---

### Post by uteck on 2011-12-25
You can delete the contents of the MBR of the other drive with;
```
dd if=/dev/zero of=/dev/hda bs=446 count=1
```
Replace hda with the proper drive.  
If you do clear the wrong drive you can reinstall grub with;
```
grub-install /dev/hda
```

---

