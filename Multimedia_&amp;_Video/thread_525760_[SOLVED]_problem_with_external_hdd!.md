---
title: "[SOLVED] problem with external hdd!"
date: 2007-08-14
forum: Multimedia &amp; Video
---

### Post by jmate24 on 2007-08-14
my computer and gparted is that gparted sees my external hdd without it being there.
and when i plug it in it(my computer/ubuntu) will not load it even though it sees it in the bios.

can anyone help me resolve this issue, i would be very greatfull.

jmate24:)

---

### Post by aysiu on 2007-08-14
Plug it in.

Paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo fdisk -l
df -h
cat /etc/fstab
``` Then paste the output back here.

---

### Post by jmate24 on 2007-08-15
thanks aysiu:)
 but it was the hard drive that was the problem, also found out that it was causing boot problems too.

---

