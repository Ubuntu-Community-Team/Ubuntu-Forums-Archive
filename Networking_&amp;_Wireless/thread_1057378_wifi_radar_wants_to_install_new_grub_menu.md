---
title: "wifi radar wants to install new grub menu"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by jesse c on 2009-02-01
installing wifi radar from terminal brings up a window that wants me to install a new grub menu but warns me that my current menu is 'locally modified' and gives me several options,like install new,leave alone,install into new shell,show differences(side by side or individually),etc.Anybody have an opinion on what will happen if i elect to install new grub?

---

### Post by Prospero2006 on 2009-02-01
Installing the new grub should be ok. I'm assuming you haven't heavily modified your menu.lst by hand. 

Here's what you do:

-Make a backup of /boot/grub/menu.lst
-Have the package manager install the new grub.

If it crashes, boot a live cd and recover the backed up file.

---

### Post by jesse c on 2009-02-01
i tried sudo /boot/grub/menu.lst but it says no such file exists

---

