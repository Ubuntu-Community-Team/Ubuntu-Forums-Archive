---
title: "Ubuntu USB interface to Nexus 7"
date: 2013-10-22
forum: Mobile Technology Discussions (CLOSED)
---

### Post by patrick_g2 on 2013-10-22
On win7, I plugged my nexus 7 into the USB port and ta-da I could see, copy and delete files on the Nexus 7 from my laptop. 

This does not appear to work on Ubuntu. I have looked and cannot seem to find any interface apps or anyone else that is trying to make this work. Suggestions please.

Patrick

---

### Post by 3rdalbum on 2013-10-23
You need Ubuntu 13.04 or above.

If you have 12.10 or below, there are several googlable workarounds using FTP servers, adb, etc.

---

### Post by alphasoup on 2013-10-26
On Ubuntu 10.4 using go-mtpfs with a little bit of coding Nexus 7 USB can be done:
[http://ubuntuforums.org/showthread.php?t=2128292](http://ubuntuforums.org/showthread.php?t=2128292)

This issue was bugging me for 6+ months, sometimes worked, sometimes failed using MTPFS.
Now go-mtpfs is rock solid (for me) on vintage Ubuntu.

---

### Post by 3rdalbum on 2013-10-28
> **alphasoup said:**
> On Ubuntu 10.4 using go-mtpfs with a little bit of coding Nexus 7 USB can be done:
[http://ubuntuforums.org/showthread.php?t=2128292](http://ubuntuforums.org/showthread.php?t=2128292)

This issue was bugging me for 6+ months, sometimes worked, sometimes failed using MTPFS.
Now go-mtpfs is rock solid (for me) on vintage Ubuntu.

I'm not sure which one I tried - probably MTPFS - but I didn't have any success on 12.10, and knowing first-hand how terrible MTP support is on Linux I just assumed it would only work with the sun in its zenith and the computer placed within a hexagon. Rather than call a witch-doctor, I took the easy way out and updated the system to 13.04, getting a few extra benefits too.

So, Patrick, if you try upgrading your MTP support on an old Ubuntu and can't get it to work, don't think there's anything wrong with you!

---

