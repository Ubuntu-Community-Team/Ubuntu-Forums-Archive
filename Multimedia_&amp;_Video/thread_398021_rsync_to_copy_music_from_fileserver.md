---
title: "rsync to copy music from fileserver"
date: 2007-03-31
forum: Multimedia &amp; Video
---

### Post by tgm4883 on 2007-03-31
I have all my music on my fileserver, but cannot access it accross the network from any of my ubuntu boxes (Using samba, ubuntu fileserver).  As I will add new music periodically to the fileserver, i would like an easy way to sync the music folder to the folder on my desktop.  I was hoping that either

a)  there was  a way to access the music accross the network without having to copy it over first.  Then I wouldn't need to sync since there would only. be one source of music.

b)  rsync would check for any new/removed music and change accordingly.  I have never used rsync before so I don't know if this sort of thing is its intended purpose.  Perhaps there is another program out there that would be better.

---

### Post by prensing on 2007-03-31
There are plenty of ways to access the files directly. I don't understand why you say you can't access them. If the server is running Linux, then the best method is NFS. Alternately, you can use SMB (Samba) for either a Windows or Linux server. If you want to mount it permanently (ie the client is not a laptop), first work out the mount options with the smbmount command, and when you have it working well, put the same options into /etc/fstab.

If you do end up keeping a copy on the local machine, then, yes, rsync is exactly what you want. You can set the server to have an open rsync server or you can run rsync through an SSH connection.

---

### Post by tgm4883 on 2007-03-31
Resource wise, it seemed silly to run both nfs and samba (need samba for windows clients)  I know I could mount the remote samba file systems, I guess I just wondered about going through the network tool and playing the file from there.

I will mount the samba file system on my desktop and do rsync on my laptop.  Thanks for the help

---

