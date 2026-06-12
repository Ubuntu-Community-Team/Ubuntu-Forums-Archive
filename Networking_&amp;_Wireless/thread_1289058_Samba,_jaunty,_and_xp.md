---
title: "Samba, jaunty, and xp"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by Sin@Sin-Sacrifice on 2009-10-12
So... took about a half an hour out of today to set up samba between the 2 PCs here and I, fairly quickly, got both sides to see folders. I even got ubuntu accessing the shared folders on xp... but the other way not so much. Funny thing is I know why and how to fix it. Why am I here? My computer told me no... well... didn't say anything but didn't do what I asked. First time in ubuntu so bare with me while the windows horrors come flooding back. Just kidding... anyway. I can't seem to change permissions of hard drives. I tried mounting it the "normal" way through the gui and it auto creates /media/disk where I sudo chmod -R 777 /media/disk. No go. I also sudo mount /dev/sdb1 /mnt/share after making that directory and still belongs to root. When I do it in the gui with a sudo nautilus it tells me the operation isn't permitted... so I guess the PC DID tell me no. I can access any shared folders I make within my home folder from XP but nothing on any other drives or that belongs to "root". Please... relieve my suffering by either giving me a solution or shooting me 'cuz that half hour turned into 3 hours now. Thanks in advance.

---

### Post by Iowan on 2009-10-12
> **Sin@Sin-Sacrifice said:**
> Please... relieve my suffering by either giving me a solution or shooting me 'cuz that half hour turned into 3 hours now.Wow, and that was at least 15 hours ago...
Besides providing a BUMP, I'll offer [this]("http://ubuntuforums.org/showthread.php?t=288534") CIFS-mounting How-To, and hope it helps.

---

