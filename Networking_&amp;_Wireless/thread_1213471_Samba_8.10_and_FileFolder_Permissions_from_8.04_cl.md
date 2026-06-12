---
title: "Samba 8.10 and File/Folder Permissions from 8.04 client"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by kendoori on 2009-07-14
I have an 8.10 workstation set up as home NAS. I've set up the box with SAMBA and since it is mixed home network, I've set security=share so that my wife and daughter don't have to deal with logging in to copy files and use the shared printer. All is fine from the Windows machines.

I'm having issues when the Ubuntu 9.04 workstations writes files/folders to the NAS. I have several shares set up on the 8.10 machine, and I have the mounted in fstab as follows:

```

# Network Shares
//Felix/Data                               /media/NAS-Data   cifs   username=me,password=&&**%%9  0  0  
//Felix/Music                              /media/NAS-Music  cifs     username=me,password=&&**%%9  0  0

```

When I drag a folder and nested files from the 9.04 machine to the NAS, by default the folder permissions are set to the ownership of my 9.04 user (not the mounting user), the group membership set to the same, and the others permission is set to None.

Question is, how can I set the others permission to "Access files" by default. I suspect that this would be somewhere in the smb.conf file on the NAS box. Would this be the create mask and directory mask settings? and if so what should I set them to.

---

