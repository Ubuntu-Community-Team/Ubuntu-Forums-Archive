---
title: "Permissions issue when mounting a remote Windows share via fstab"
date: 2013-06-23
forum: Networking &amp; Wireless
---

### Post by smeep on 2013-06-23
Hi there, I have an Ubuntu 12.04 LTS box that mounts a remote Windows share via an entry in fstab.  The share does mount and I can read and write to it just fine.  What doesn't work is changing permissions on files stored in this share.  For example, chmod o-x /media/tm/file1.txt doesn't give an error, but it also doesn't change anything.  From the Ubuntu GUI, if I try to change anything in the Permissions tab of the file's properties then it instantly snaps back to the original value.  When this happens, the "Last changed" date field in this tab briefly flashes today's date and time but then returns to the original last changed timestamp.

How do you mount a share such that permissions of the share's contents can be changed?

My fstab entry looks like this:
```
//server/share /media/tm cifs credentials=/home/tm/.smbcredentials,_netdev,users,uid=smeep,gid=smeep,iocharset=utf8,sec=ntlm 0 0
```

Thank you!  I'm really stuck on this.

---

### Post by marvselby on 2013-06-23
I'm going to try the easy answer (or question) first.  Did you try **sudo** chmod o-x /media/tm/file1.txt?  That gives you root permissions.  From the GUI you could use (from the prompt) something like "**sudo** nautilus"

---

### Post by prodigy_ on 2013-06-23
> **smeep said:**
> chmod o-x
That won't work on Windows shares. Windows ACLs are not compatible with Linux permissions. You could use **setcifsacl** command but it's not very intuitive.

Also **users** implies **noexec**, so you wouldn't be able to execute files from the share anyway (at least not directly). Something like **bash /media/sharename/filename.sh** would still work but for that you don't need to modify permissions at all. 

See **man mount** for more info.

---

### Post by smeep on 2013-06-26
Thanks guys, I appreciate your help.

I did specify "sudo", but it's good that you asked. :)

Yeah, it looks like the permissions (and extended attributes) of files on Windows shares cannot be changed from within Linux.  It looks to me as if Linux mounts the Windows share using whatever Windows user/password you specify, and then Linux sort of superimposes its own fabricated permissions onto the files (like if you specify file_mode and dir_mode).  I hadn't realized it worked that way.

---

