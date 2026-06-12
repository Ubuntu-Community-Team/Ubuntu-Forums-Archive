---
title: "Permissions on shared directory, redux"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by jazzgossen on 2009-01-22
I'm trying to set up a shared directory with read/write permissions for all users in the "local" group, and no permissions for anyone else. I've used ACL as described in [this thread]("http://ubuntuforums.org/showthread.php?t=145741"), which works fine as long as I'm logged in to the computer where the shared directory is.

However, I have my shared partition mounted with NFS, and when I create new files or directories over either NFS or SSHFS, they get permissions rw-r-x--- (for files) and rwxr-sr-x (for directories), which means that the other users can't write to files or directories. The ownership is setup as I want though, with the current user as owner and the group "local". 

Running "getfacl" results in the following:
```

$ getfacl .
# file: .
# owner: martin
# group: local
user::rwx
group::rwx
other::r-x
default:user::rwx
default:group::rwx
default:other::r-x

```

So the permissions *should* be rwxrwxr-x, and they are when I log in (via SSH) to the host and create files there as any user in the "local" group.

What do I need to do to make this work over NFS or SSHFS too?

---

### Post by Gamzarme on 2009-01-22
I am having the same problems. I cannot for the life of me figure out how to force rwx permissions for the group. rwx is set for the owner but I am wondering if there is a way to force rwx for group as well.

I realize that the default Ubuntu behavior is the create files and directories with the "drwxr-xr-x" permissions (at least for directories). However I have a NFS share mounted and it uses this same, default behavior. Is it possible to have files and directories created with the "drwxrwxrwx" permissions? I also have the same drive exported and mounted via Samba and it creates "drwxrwsrwx" permissions properly, however Ubuntu over NFS does not.

Thanks for the initial posting, Jazz!

Regards,

Patrick

---

### Post by jazzgossen on 2009-01-31
After a little bit of googling, it appears that ACL over NFS is not possible witk standard Ubuntu. It seems that the only solution is to recompile the kernel or install some other distro, such as Suse or Fedora, where ACL over NFS is supported.

---

