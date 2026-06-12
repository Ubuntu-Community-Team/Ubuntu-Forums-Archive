---
title: "transferring files"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by bradpurvis on 2010-07-14
i have two pcs on the same wireless network

ubuntu 10.04

windows xp sp3

i have about 24GB of data that needs to be transferred to the windows pc. is there a decent utility for doing this that is compatible? 

need an answer asap

---

### Post by ajgreeny on 2010-07-14
Samba will do that, though never having needed to use it, I can't tell you more.

---

### Post by YesWeCan on 2010-07-14
Two ways:
1) Create a public share folder in XP. Use Ubuntu's Nautilus to open it (Places/Connect to server/Windows share). Drag and drop.

2) Create a public share folder in XP. Install 'smbclient' in Ubuntu (may already be installed). Mount the Windows folder:
sudo mount -t cifs //xp-ip-address/xp-folder-name /local-mount-path -o username=windows-user,password=windows-password,rw
Then copy the files from a  terminal.
Then sudo umount -t cifs /local-mount-path

---

