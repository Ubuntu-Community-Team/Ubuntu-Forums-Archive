---
title: "How-To enable ACX-111 Wireless Cards after upgrading Drake Kernel"
date: 2006-07-15
forum: Networking &amp; Wireless
---

### Post by southerngrey on 2006-07-15
If your ACX-111 Wireless card stops working after ugrading your kernel in Dapper Drake this is the solution:

- There is a bug where a default firmware link is pointing to the wrong place see [http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu)

- The easiest fix is to delete and recreate the link, pointing it to the right location. The link you want to change is /lib/firmware/"insert current kernel version here"/acx/default/tiacx111c16 it points to the tiacx111c16 file in the 2.3.1.31 folder you need to move this to point to the file in 1.2.1.34

Go into terminal and type

cd /lib/firmware/"insert current kernel version here"/acx/default/
oress enter, then type

sudo rm /lib/firmware/"insert current kernel here"/acx/default/tiacx111c16
press enter, then type

sudo ln -s /lib/firmware/"insert current kernel here"/acx/1.2.1.34/tiacx111c16
press enter.

Reboot.

This should get the ACX-111 wireless card working.

---

