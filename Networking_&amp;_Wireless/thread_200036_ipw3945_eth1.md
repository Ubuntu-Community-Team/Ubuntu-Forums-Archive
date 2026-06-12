---
title: "ipw3945 eth1"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by chrismiceli on 2006-06-19
I have an inspiron e1505 laptop running ubuntu.  It has a ipw3945 wireless card on eth1 but ubunut doesn't see eth1```
eth1 no such device
```  How can i get ubunut to see this device?
Thanks

---

### Post by ngeren on 2006-06-19
Mine worked fine before last nights package update, now it won't even find my device.

---

### Post by ngeren on 2006-06-19
Reverting back to the 2.6.15-23 kernel got my wireless working again. Obviously the recently (updater-installed) 2.6.15-25 kernel has some issues. Q/A might have been high?

---

### Post by chrismiceli on 2006-06-20
I have the 2.6.15-25 kernel how do i get to the other kernel (it's not in my bootloader) and how would I upgrade back?  What should I do?

---

### Post by ngeren on 2006-06-21
Did you check the boot directory to see if it exists in there? If so, you should be able to easily add it to the bootloaders menu (/boot/grub/menu.lst).

---

