---
title: "Sharing Internet"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by Atrus6 on 2008-12-21
On Windows there is a checkbox that allows other devices to use a computers internet connection.  What would allow me to accomplish the same thing through ubuntu?

---

### Post by Iowan on 2008-12-21
It's a bit more involved, but check [here.]("https://help.ubuntu.com/community/Internet/ConnectionSharing")

---

### Post by Atrus6 on 2008-12-21
Okay, and where would I find the names of the devices?  I am using a USB wireless adapter (which works wonderfully on Ubu, and horribly on XP) and my built-in NIC.

---

### Post by Iowan on 2008-12-21
*/etc/network/interfaces* would be one place to check.
**ifconfig -a** might be another.

---

