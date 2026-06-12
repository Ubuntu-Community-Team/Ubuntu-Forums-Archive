---
title: "New drives suddenly appeared."
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by Jake808 on 2007-06-05
I have noticed recently that after doing a software update on Ubuntu 7.04, I have two extra cd-rom drives showing up on Computer in the file browser. They are named cd rom 1 and cd rom 2. These are in addition to my physical cd drive and my dvd-r drive. Why have they appeared? When I click them it just says unable to mount drives.

Jake

---

### Post by rfurman24 on 2007-06-05
Open a terminal and type the command "sudo gedit /etc/fstab" without the quotations. Delete the lines regarding your cdrom drives as they should not be in /etc/fstab. It seems to be a problem with the kernel update.

---

