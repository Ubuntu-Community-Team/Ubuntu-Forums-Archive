---
title: "aircrack error - fwrite: read-only system"
date: 2013-06-23
forum: Networking &amp; Wireless
---

### Post by nomaam on 2013-06-23
Hello:

I am running the newest version of Backtrack and am testing my wifi network with aircrack. Backtrack is installed on its own partition and has lots of storage space. 

I have never had this problem before but when I run aircrack / airodump, when testing WEP, after about a minute of gathering packets everything comes to a halt with the following error

"
fwrite(packet data) failed: Read-only file system
"

I then have to restart using the boot disc in forensic mode and run

fsck /dev/sdb5

This fixes the drive and I can now boot again and start running programs. However, this error now happens every time after about a minute of gathering packets and I have had to recover the drive several times. 

Could someone please suggest a way to repair this problem? (short of a reformat and reinstall of everything)

I tried asking this question on the Backtrack forum but they have disabled new account registration. 

Thank you.

---

### Post by wildmanne39 on 2013-06-23
Hi, aircrack is not supported on the ubuntu forum, you will need to get help on the backtrack forum or I believe aircrack now has its own forum.

Thread closed!
Thanks

---

