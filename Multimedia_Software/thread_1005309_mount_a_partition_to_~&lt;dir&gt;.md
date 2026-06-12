---
title: "mount a partition to ~/&lt;dir&gt;"
date: 2008-12-08
forum: Multimedia Software
---

### Post by leg on 2008-12-08
How do I do this? I have a partition that is used just to store music files and I would like to mount it on the mount point ~/music for each user. How do I do this in fstab? is the tilde expanded in this situation?

---

### Post by ajgreeny on 2008-12-08
As fstab loads before any user logs in, you will need to give the full path to the mount point in the fstab entry ie, /home/username/music.  If you use the ~ fstab will be completely baffled as there will be no ~/music available to it.  Apart from that I can see no major reasons why this should not work, though I have never tried it personally.

I am not sure how you would deal with multi users, apart from mounting the partition several times with their own entries in fstab, once for each user, and to be perfectly honest, I don't know if a partition can be mounted more than once at the same time by the system, eg, can it be mounted to /home/user1/music and also to /home/user2/music at the same time.  No doubt others with more knowledge will be able to tell you about that.

---

### Post by exodus_ on 2008-12-08
> **leg said:**
> How do I do this? I have a partition that is used just to store music files and I would like to mount it on the mount point ~/music for each user. How do I do this in fstab? is the tilde expanded in this situation?

Your best bet to accomplish this would be to mount the partition somewhere else in the filesystem on say /media/music and then create symlinks in the users home directories.  You could add the symlink to /etc/skel so any new user will have this in their home.

You could also set up in the login script to "bind" mount the mount in their home directory (mount --bind /where/you/mounted/the/dir /home/username.here/Music)

Hope this helps

---

### Post by leg on 2008-12-08
Thanks I think the sim link will be the best idea.

---

