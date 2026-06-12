---
title: "Domain privs working via gvfs but not regular mount command"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by alistair.mckenzie on 2010-12-14
I have a samba based domain controller which has a share with limited privileges for different usernames.  When I log in the gvfs wizard in ubuntu everything is all good and I can access all the files I am supposed to be able to.

In the wizard I specify the hostname, username and domain and the string it uses is:
***smb://domain;user@host/share/***

I try mounting the same share to /mnt/hostname using the following command:
***mount -t smbfs //host/share -o username=domain\\user /mnt/hostname*** 
and after supplying the password I cd to a subdirectory of the mounted directory and I get Permission Denied.

I suspect it has to do with the owner and group of the directory not being a user in the local machine.  When mounted via gvfs the owner and group are the local user and group whereas when mounted via the mount command the user and group are foreign uids and gids.

I had thought that gvfs would have relied on mount() system call under the bonnet but is this not the case as gvfs mounts don't appear in the list when you type 'mount'.

Can this be solved in the standard smbfs mount or is gvfs simply a better implementation that does some magic behind the scenes to set the owner and groups in accordance with the smb protocol?

---

### Post by alistair.mckenzie on 2010-12-14
For any interested readers, With some further digging around in man pages I managed to solve this using the uid and gid options of the mount command.

ie using.
***mount -t //host/share -o username=user,uid=localuser,gid=localgroup,password=password /mnt/host***

---

