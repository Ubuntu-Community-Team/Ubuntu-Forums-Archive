---
title: "basic file share with 8.04 (ubuntu to ubuntu) how to please?"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by candtalan on 2009-06-15
I want to arrange a shared directory on a machine (No1) on a LAN so that the directory can be seen and written to from another machine (No2) on the same lan. Both machines are ubuntu 8.04.

On the sharing machine (1) when I look at the directory which is proposed to be shared, and right click, I do not see any option to invoke sharing.

The Machine (2) used to be windows xp and this sharing was set up ok at that time, but since going to ubuntu I somehow have lost the configuration, which was presumably samba, which may not be best appropriate now anyway.

comments would be most welcomed
tia

---

### Post by aromo on 2009-06-15
Use NFS if both system are *nix.  Use Samba if you want to share with Windows computers.

---

### Post by superprash2003 on 2009-06-15
here's a guide [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by Iowan on 2009-06-15
It *can* be done via Samba - but it's somewhat complex (after all, it was designed to work with Windows ;) )> **aromo said:**
> Use NFS if both system are *nix.+1

---

### Post by dmizer on 2009-06-15
The above howto is overly complex for most situations. Please see the 4th link in my sig for a simple share configuration.

---

