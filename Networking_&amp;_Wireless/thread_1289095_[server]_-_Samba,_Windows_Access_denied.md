---
title: "[server] - Samba, Windows Access denied"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by iarp on 2009-10-12
Hey, Ubuntu Server 9.04

Config for the share:
#########
[files]
path = /home/iarp/www/files
browseable = yes
writable = yes
read only = no
create mask = 0777
guest ok = yes
#########

No matter what i try from all my googling about this problem, nobody's configuration seems to work. And now i'm stuck. Which is giving me the actual problems, stupid windows or config problems? Oh ya, if i map a network drive in windows to the folder, and login with different credentials that of which is on the linux box... everything works fine.

---

### Post by xman958 on 2009-10-12
Please do, and try

sudo chmod a+rwx /home/iarp/www/files

---

