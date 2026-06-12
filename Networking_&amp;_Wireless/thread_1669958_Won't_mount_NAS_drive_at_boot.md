---
title: "Won't mount NAS drive at boot"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by frkstein on 2011-01-18
I am having a small issue on my machine. I have a NAS drive serving up media files. I have a line in my /etc/fstab such that, when the mythbuntu machine boots it is supposed to mount the network drive. This configuration worked fine for mythbuntu 9.10. I recently updated the machine up to 10.10 and since then the network drive won't mount at boot. If I open a terminal and issue: sudo mount -a, it will mount the network drive just fine. Does anyone have any ideas what is going on?

---

### Post by andysummerskill on 2011-02-03
I've got exactly the same problem.

I upgraded from 9.10 to 10.04 and (I haven't changed my fstab file) and my nas drive does not mount on boot anymore, but will mount with the command sudo mount -a.

the relevant line in fstab is:

//192.168.1.66/public /mnt/mss-038100 cifs rw,mand 0 0

Anyone got any ideas?

---

