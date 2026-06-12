---
title: "Windows won't authenticate samba shares for guest access"
date: 2013-06-12
forum: Networking &amp; Wireless
---

### Post by Andres Gonzalez on 2013-06-12
I am trying to setup samba shares for guest access for my home network. All I want to do is provide guest access so each family member has a remotely accessible directory so they can copy over files they want to backup. I do not want to give family members user accounts on the linux box, just guest access for samba. This is an example of one of my shares in my smb.conf file:

security = share

[Backups-Rhonda]
path = /raid1/rhonda
guest ok = yes
guest account = nobody
guest only = yes
browseable = yes
writable = yes

The shared paths have file permissions 666. I used smbpasswd to give a password to the nobody account on my debian box. Using smbstatus -v I can see that the Service is indeed connected to the Windows client. On the Windows clients I can see the shares so samba appears to be working. 

However, the authentication fails on the Windows boxes. I always get a dialog that says "You do not have permission to access....."   I have tried "map network drive..." but that fails with a "Location is not available W:\ is not accessible Access is denied" dialog. I tried the "Connect using different credentials" under Map Network Drive, but still the same error dialog.

How do I get the Windows boxes to authenticate properly for simple guest access?

---

