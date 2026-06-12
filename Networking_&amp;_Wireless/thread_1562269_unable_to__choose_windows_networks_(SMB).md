---
title: "unable to  choose windows networks (SMB)"
date: 2010-08-27
forum: Networking &amp; Wireless
---

### Post by ocelot666 on 2010-08-27
When I go to share a folder I do not have the option to select windows networks (SMB). Only the unix service.. I am running  ubuntu 10.04 thanks for any help

---

### Post by jimbop99 on 2010-08-27
Have you installed samba?

---

### Post by Morbius1 on 2010-08-27
Based on your description you're using "shares-admin". That no longer works.

You need to install:
```
system-config-samba
```After it's installed it will be at System > Administration > Samba

Or you can forget both and use Nautilus to create your samba shares:
Nautilus > Right Click a folder > Sharing Options

---

### Post by endotherm on 2010-08-27
> **Morbius1 said:**
> Based on your description you're using "shares-admin". That no longer works.

You need to install:
```
system-config-samba
```After it's installed it will be at System > Administration > Samba

Or you can forget both and use Nautilus to create your samba shares:
Nautilus > Right Click a folder > Sharing Options
really? I was under the impression that shares-admin still worked for setting workgroups and setting smbpasswd for users. at least it seems to work on my network. am I missing somthing?

---

### Post by Morbius1 on 2010-08-27
If you got it to work that's great but for most folks shares-admin doesn't recognize that samba is installed so you end up in an infinite loop of being asked to install samba every time you open the application. Or it will open and smb is grayed out.

I use Nautilus-share immediately after installing a new OS to make sure samba works. Nautilus-share will install samba on first use. When I then launch shares-admin it asks me if I want to install samba and NFS. If it ain't broke it looks a little peakid.

system-config-samba doesn't have this complication.

---

### Post by ocelot666 on 2010-08-27
I am running Samba. Your right about the SMB being grayed out. ill remove nautilus and reinstall it see if it works thanks again.

---

### Post by Morbius1 on 2010-08-27
I sincerly hope you didn't mean "remove nautilus". Nautilus is more than a file manager in gnome. You really didn't have to remove anything.

---

