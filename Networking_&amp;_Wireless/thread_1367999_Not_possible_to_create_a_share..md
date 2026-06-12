---
title: "Not possible to create a share."
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by Kris Vansteenkiste on 2009-12-30
***Unable to create shares.***
I installed Samba on my Ubuntu (Karmic). I did this before installing all the updates. Now, I cannot create a share: if I click a folder to share it and ask to add the permissions, I get to see an error pop-up with: 'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.
 
***Unable to reinstall Samba.***
Then I removed Samba (sudo apt-get remove samba) and reinstalled it, but I get to see an error message:
Fetched 1,840kB in 1s (1,268kB/s)
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 160019 files and directories currently installed.)
Unpacking samba (from .../samba_2%3a3.4.0-3ubuntu5.1_i386.deb) ...
Selecting previously deselected package smbfs.
Unpacking smbfs (from .../smbfs_2%3a3.4.0-3ubuntu5.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Processing triggers for ureadahead ...
Setting up samba (2:3.4.0-3ubuntu5.1) ...
update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode.
Generating /etc/default/samba...
 * Starting Samba daemons                                                       Segmentation fault
                                                                         [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up smbfs (2:3.4.0-3ubuntu5.1) ...
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

