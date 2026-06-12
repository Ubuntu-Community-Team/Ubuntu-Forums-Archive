---
title: "CIFS/NTFS Share Mounting Error w/return code = -13"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by holodad on 2009-03-20
Hello Guys,

I had a small problem after switching from Gnome to XFCE4 on a 8.10. I don't knwo if it's related because some other packages was upgraded since i performed an upgrade with the up manager before... However, if you are trying to mount a Windows Share with CIFS, you might get this message when entering this command: sudo mount -t cifs -vvv -o user=xxxx //w2KShare/Folder /media/XXXXX

"Mounting the DFS root for a particular server not implemented yet
No ip address specified and hostname not found"

and:

[ 4459.837889] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
[ 4459.837908]  CIFS VFS: Send error in SessSetup = -13
[ 4459.971000]  CIFS VFS: cifs_mount failed w/return code = -13

To resolve this issue, you just need to mount the CIFS with this command:

sudo mount.cifs //w2KShare/Folder /media/FOLDER -o user=XXXX

It works

---

