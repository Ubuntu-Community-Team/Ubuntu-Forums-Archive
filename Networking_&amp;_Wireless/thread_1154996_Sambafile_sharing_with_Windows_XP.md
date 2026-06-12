---
title: "Samba/file sharing with Windows XP"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by NvidiaN on 2009-05-10
Hello all,

Could anyone possibly tell me how to get from my laptop (Kubuntu, Jaunty), to see my room-mates windows XP computer, on which I have all of my files from Windows. I installed samba using terminal (sudo apt-get install samba), but I don't see any new options, nor new programs, or anything.

I'm very noob, so the simplest explanations would be greatly appreciated!

<3

---

### Post by Iowan on 2009-05-10
What (I think) made my laptop (recent Jaunty install) see my Samba network was installing Winbind, editing /etc/nsswitch.conf to include "wins" before "dns" and verifying that the workgroup setting (in /etc/samba/smb.conf) was the same as rest of network. I opted for a reboot (rather than just restarting associated services) to insure everything got activated.

---

