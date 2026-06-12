---
title: "Wired Network doesn't work"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by njb on 2009-06-28
Hello,
I'm using 9.04 and recently I made an update.
After this the system asked for rebboting computer.
When I rebooted I lost my wired network and get the message peripheral not managed.
I'm obliged to use the wireless lan is is much more slow.

:lolflag:

NjB

---

### Post by Iowan on 2009-06-28
Check contents of */etc/network/interfaces*. If you use DHCP, the file *should* contain only the definition for loopback (lo).  **lshw -C network** might reveal some more information.

---

### Post by njb on 2009-06-29
Thank you IoWan,

Here is the solution :

sudoedit /etc/NetworkManager/nm-system-settings.conf

edit the file to read
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

save and reboot.

:lolflag:


I found this in this thread at :

[all variants] Known Jaunty Wireless/Ethernet workarounds

---

