---
title: "set umask for creating files in CIFS mount"
date: 2011-12-13
forum: Networking &amp; Wireless
---

### Post by scido06 on 2011-12-13
Hi,

I'm struggling since several days on CIFS permission.

I've got a NAS (Verbatim gigabit) with samba 3.0.25a. Via telnet I found its smb.conf and I have "create mask=0775" and "directory mask=0775" set properly.
When I mount the share from my ubuntu 10.10 and create a new file, I have a 755 mode permission, instead a 775 as in the server's smb.conf. It seems that my umask (022) on ubuntu overwrite the server's umask (002). Is it a way to change this behaviour?

I found a strange error in my client's log for CIFS mount: "*CIFS VFS: server 192.168.1.253 of type Samba 3.0.25a returned unexpected error on SMB posix open, disabling posix open support. Check if server update available.*" Can it be related (of course I cannot update the samba server, until a new firmware will be available?

I've already tried the file_mode and dir_mode options, but nothing change. The same with "noperm" option. I tried "nounix" option too, but after mounting I cannot see the folders I have in my share! No solution so far (I change my umask in ubuntu - umask 002 in ~/.profile, but I'd like a solution only for CIFS share)!

Please Help!

thank you,
Scido

---

### Post by scido06 on 2011-12-14
Bump

---

