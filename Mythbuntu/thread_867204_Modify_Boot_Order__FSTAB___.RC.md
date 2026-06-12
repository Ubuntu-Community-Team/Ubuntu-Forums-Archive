---
title: "Modify Boot Order  FSTAB /  .RC"
date: 2008-07-22
forum: Mythbuntu
---

### Post by Chewiesw on 2008-07-22
Hi

I need some help possibly modifying the boot order/sequence.

I have successfully mounted my music/videos shares in FSTAB, which should in theory remain in place through reboots. They don't and I get error messages during the boot process.

I think this is due to the fact the I am using a wireless network card and the wireless card boots on start up via a .RC file. 

Now my hunch is that the fstab file loads before the rc file.

Once everything has booted I can run the mount -a cmd from a terminal and all the mounts are back and I can browse for my music again.

Is there anyway I can speed up the wireless connection or delay the mount process?

---

