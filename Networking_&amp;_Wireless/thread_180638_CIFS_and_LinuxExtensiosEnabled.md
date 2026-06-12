---
title: "CIFS and LinuxExtensiosEnabled"
date: 2006-05-22
forum: Networking &amp; Wireless
---

### Post by jferrando on 2006-05-22
I have been using CIFS with some problems, now together with sshfs user-mode filesystem. CIFS seems more robust, it is supposed to have file locking, though not working very well with OpenOffice.
I mount the share with:

# mount -t cifs //192.168.8.5/datos /home/jferrando/csurera -o credentials=/etc/smbc.jordi,uid=1000,gid=1000,iocharset=utf8
# echo 0 > /proc/fs/cifs/LinuxExtensionsEnabled

However, the user can't see the share files with the right permissions. It worked fine once, but I don't know where is the problem now.
I have a samba server "Samba version 3.0.22" with
unix extensions = yes

I would like to use CIFS with the server's user's permissions, but the UIDs and GIDs are different from my ubuntu client. I have even installed LDAP pam.d authentication on the ubuntu dapper client, but in this case the user can't share local groups and so it can't sudo, use the audio, etc.
Too complex right now for the ubuntu desktop client be mature as a Windows alternative for the non-geek user.

---

