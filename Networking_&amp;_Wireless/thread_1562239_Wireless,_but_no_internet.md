---
title: "Wireless, but no internet"
date: 2010-08-27
forum: Networking &amp; Wireless
---

### Post by idefix_7 on 2010-08-27
I'm facing [same problem]("http://ubuntuforums.org/showthread.php?p=9772629")...got wireless connection but no internet access.
I do not understand what to do with the MAC address on my router !? The address is visible so I presume it is correct connected.

---

### Post by Iowan on 2010-08-27
Moved to new thread from [http://ubuntuforums.org/showthread.php?p=9772629]("http://ubuntuforums.org/showthread.php?p=9772629")

---

### Post by JamesHayek on 2010-08-27
I just faced this problem, see here:

[My Issue addressed at this forum. [Resolved]]("http://ubuntuforums.org/showthread.php?t=1560968")

Run: ```
sudo dhclient -r
```

and then ```
sudo dhclient
```

Make sure you reset the router.

It is probably the router not assigning a DHCP lease. reset the router, set it to no encryption and try to connect once again.

---

