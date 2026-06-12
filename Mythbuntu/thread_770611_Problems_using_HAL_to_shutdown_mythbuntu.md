---
title: "Problems using HAL to shutdown mythbuntu"
date: 2008-04-27
forum: Mythbuntu
---

### Post by skg on 2008-04-27
Hi

I'm trying to use the HAL scripts to halt my mythbuntu mediecenter from mythwelcome, but when i execute /usr/share/mythtv/myth-halt.sh I get the following error.

stefan@mediecenter:~$ /usr/share/mythtv/myth-halt.sh 
Error org.freedesktop.Hal.Device.PermissionDeniedByPolicy: org.freedesktop.hal.power-management.shutdown-multiple-sessions no <-- (action, result)

Any suggesting how to fix this?

Best regards
Stefan

---

### Post by laga on 2008-04-27
Is another user logged in at the same time? Either in X or in VNC?

---

### Post by skg on 2008-04-27
It is a 64 bit mythbuntu 8.10, which I've just upgraded.

---

### Post by skg on 2008-04-27
No, but by ssh.

---

### Post by skg on 2008-04-27
I still doesn't halt even if i log out of the ssh session.

The mythbuntu installation is a combined setup, with both frontend and backend on the same PC.

---

### Post by superm1 on 2008-04-27
I believe you will "only" be able to do this from a logged in session.  Eg, not via ssh, a VNC, or a different X session.

---

### Post by drifting on 2008-05-18
Ok, if I understand this right? within Mythtv general I put under the shutdown section \usr\share\mythtv\myth-hal.sh  

That it should now shutdown ?  Mine don't. And I get the same permissions error.

Regards

Paul.

---

