---
title: "Intrepid Cannot print to Windows Samba on XP - HP Deskjet D2560"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by BigBaka on 2009-05-16
Dear all,

I've been looking into resolving an issue I have trying to print to an HP Deskjet on a Windows XP network via samba. Followed the standard tutorial, and then came across the following thread [http://ubuntuforums.org/showthread.php?t=680590](http://ubuntuforums.org/showthread.php?t=680590) and followed everything in here, but still cannot print. When I print a test page it goes into the spool of the Windows machine, but then sits there and eventually comes up with printing error in the windows spool.

I have reset my workgroup to the MS default MSHOME, and I have reinstalled the printer on the windows machine giving it the simple name of Deskjet. The samba pathe is configured to smb://MSHOME/HP/Deskjet. Tried to put in :USB001 as the port but that screwed up the process and the file didn't even get through to the PC. Have also tried putting in the fixed IP address of the XP machine (as per the thread above) in the samba path but didn't make any difference. I'm clean out of ideas! Can anyone help.

Regards,
BB

---

### Post by BigBaka on 2009-05-16
Hmm, came in this morning, changed the path in samba to an ip address instead of windows computer name, and somehow it worked. Very strange, but at least I can now print to my networked printer.

---

