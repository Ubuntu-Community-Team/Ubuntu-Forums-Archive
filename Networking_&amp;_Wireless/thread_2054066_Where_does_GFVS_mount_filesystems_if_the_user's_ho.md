---
title: "Where does GFVS mount filesystems if the user's home directory is an NFS share?"
date: 2012-09-06
forum: Networking &amp; Wireless
---

### Post by adamltaylor on 2012-09-06
On Ubuntu 12.04, GVFS mounted volumes normally show up in the filesystem in the directory ~/.cache/gvfs .  However, if the user's home directory is an NFS share, they do not seem to show up there.  Does anyone know where they _do_ show up in this case?  I've tried

```

gvfs-mount --list --detail

```but that doesn't seem to say where in the filesystem each volume is mounted.

Can I somehow get this information out of gvfs-fuse-daemon?

Thanks in advance,
Adam

---

### Post by LewisTM on 2012-09-06
What does the [FONT="Courier New"]mount[/FONT] command tell you?
Mine says an SFTP connection is mounted in /home/me/.gvfs
I think I saw [somewhere]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/435719") that gvfs-fuse should put stuff in a random /tmp subdirectory in the event of a NFS home, but I don't know if that ever got implemented.

Cheers!

---

### Post by adamltaylor on 2012-09-07
Thanks, LewisTM, for your response!

My GVFS-mounted shares do not show up in the output from "mount" at all:

```
taylora@taylora-ws:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
/dev/sdb2 on /lhome/adam type ext4 (rw,nosuid,nodev,relatime,user_xattr)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
dm11.janelia.priv:/ifs/groups/scicomp/home/taylora on /home/taylora type nfs (rw,nolock,hard,intr,nfsvers=3,tcp,sloppy,addr=10.40.6.132)
taylora@taylora-ws:~$ 
```About this:

> I think I saw [somewhere]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/435719")  that gvfs-fuse should put stuff in a random /tmp subdirectory in the  event of a NFS home, but I don't know if that ever got implemented.I had a similar experience.

It seems like maybe I could try setting the XDG_RUNTIME_DIR environment variable, but I haven't tried that yet.

Adam

---

### Post by LewisTM on 2012-09-07
So here's my question: can you still open network files though gvfs using say LibreOffice? Some apps like LO need access to the FUSE mount while a few others like file managers don't actually need it, they talk to GIO/gvfs directly.

If you can't, you can try running
```
/usr/lib/gvfs/gvfs-fuse-daemon <local mount point>
``` 
and see if that helps. The [FONT="Courier New"]mount[/FONT] command should have a new entry for gvfs-fuse-daemon.

---

### Post by adamltaylor on 2012-09-07
I *can* open files on SMB shares in LibreWriter.  I have to click on the share in the right-hand "Places" panel in the file chooser dialog, but I can open files and read them.

Adam

---

### Post by LewisTM on 2012-09-07
Right, I forgot that LO could do that.
But can you open a Writer file from within a file manager?

---

