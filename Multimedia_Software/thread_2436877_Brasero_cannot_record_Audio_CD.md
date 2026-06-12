---
title: "Brasero cannot record Audio CD"
date: 2020-02-14
forum: Multimedia Software
---

### Post by mikeiott on 2020-02-14
Also installed K3b and it tells me I do not have rights to use cdrecord. I am the administrator. What's going on with this?

---

### Post by Holger_Gehrke on 2020-02-15
Check your group memberships with the 'groups' command in a shell. If you are not a member of the group 'cdrom', add yourself to the group with 'sudo usermod --append --groups cdrom username' (you will be asked for your password which will not be echoed in any way; replace 'username' with your username). The device file for the CD / DVD recorder (not the symbolic links /dev/cdrom, /dev/cdrw, /dev/dvd or /dev/dvdrw but the device file those links point to, usually /dev/sr0) is owned by root and is readable and writable by the group cdrom.

Holger

---

