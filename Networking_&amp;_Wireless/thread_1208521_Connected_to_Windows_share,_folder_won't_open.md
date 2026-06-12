---
title: "Connected to Windows share, folder won't open"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by alexlafreniere on 2009-07-09
So I got my Linux box to authenticate to an Active Directory domain so it could grab files off a shared drive, and it "sees" the drive, and is connected to it (the computer it's in responds to ping and hostname lookup) but Gigolo won't open the drive in Thunar so I can grab the files off of it. Does anyone know of a solution that would allow me to open this drive? Could it be that Gigolo is using the smb:// protocol/ Any help would be much appreciated.

---

### Post by alexlafreniere on 2009-07-09
Okay I used smbclient to get to the share, everything works now.

---

