---
title: "Issue with mount.cifs"
date: 2011-11-25
forum: Networking &amp; Wireless
---

### Post by sreecanthr on 2011-11-25
Dear all,
        I am having a hard time figuring out an issue while trying to mount a windows share in Ubuntu 10.04.

_Issue:_
   The problem is I am not able to mount a windows share using a serverLocalUser present in the windows-server. But I am able to use smbclient to access that same share using that same serverLocalUser. I am also able to mount the same share using a domain user who also has permission for that folder.


**sudo mount.cifs //192.168.5.61/Share /mnt/share/ -o username=serverLocalUser,password=passcode**
[I]mount error(13): Permission denied
Refer to the mount.cifs(8 ) manual page (e.g. man mount.cifs)[/I]

_Troubleshooting done:_
The following works:
[LIST=1]
[*]**smbclient //192.168.5.61/Share -U localServerUser**
[*]**sudo mount.cifs //192.168.5.61/Share /mnt/share/ -o username=domainUser,password=passcode**
[*] Mounting using the localServerUser using nautilus (which uses smbclient internally)
[/LIST]

The following does not works:
[LIST=1]
[*]**sudo mount.cifs //192.168.5.61/Share /mnt/share/ -o username=serverLocalUser,password=passcode,domain=WORKGROUP**
[*]**sudo mount.cifs //192.168.5.61/Share /mnt/share/ -o username=192.168.5.61\serverLocalUser,password=passcode**
[/LIST]

Thanks in advance for your help.

Regards,
Sree

---

