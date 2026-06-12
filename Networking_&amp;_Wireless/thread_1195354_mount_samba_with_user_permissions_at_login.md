---
title: "mount samba with user permissions at login"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by BFG on 2009-06-23
I have a NAS with the /home folder mounted using NFS and AutoFS.  This works well.

I also have a number of network volumes which are currently mounted using fstab and a credentials file.  This is done by having a generic account with its password in the credentials.

However we are now moving to a point where each user needs to mount these volumes using their own credentials.

An easy way would be to use .bash_profile, but of course mount needs root access.

Lots on the forum and interweb, but nothing conclusive.  Any help appreciated.:)

---

### Post by BFG on 2009-07-02
No-one?

---

### Post by dmizer on 2009-07-02
Please see the 2nd link in my sig. :)

Argh ... never mind.

I don't know much about it, but you'll probably want to do some research on pam mount.

Edit:
Perhaps this is a good place to start -> [https://wiki.ubuntu.com/MountWindowsSharesPermanently#Mount%20password%20protected%20network%20folders%20without%20credentials%20file%20using%20libpam_mount](https://wiki.ubuntu.com/MountWindowsSharesPermanently#Mount%20password%20protected%20network%20folders%20without%20credentials%20file%20using%20libpam_mount)

---

### Post by BFG on 2009-07-03
Thanks dmizer,

I'll check that out.  Also, I wonder if tackling this via mount is the right way.

I have a NAS mounted folder, which is shared with multiple users.  
E.g.
/media/Software >> //library/Software 

All users use this folder.  But new files should have a UID matching the user who created the file, not the user who mounted the volume.
AutoFS does this perfectly with NFS mounts, but I can't get it to work with samba.

I hope libpam_mount can let two users mount the same remote folder at the same time.  I'm going to have to umount everything and experiment.

EDIT:  EXPERIMENTING

Edit:  Hmm.  Getting a bug in libpam_mount:
[https://bugs.launchpad.net/ubuntu/+source/libpam-mount/+bug/332833](https://bugs.launchpad.net/ubuntu/+source/libpam-mount/+bug/332833)
Minor. Annoying to see the message.

I got this to mount a folder. 
```
<volume fstype="cifs" server="library" path="GUEST_SHARE" mountpoint="/media/GUEST_SHARE" options="iocharset=utf8,uid=%(USER),gid=users,dir_mode=0700,file_mode=0600" />
```

But, no other users can mount the volume on the same mount point, which is fair enough, this fixed:

```
<volume fstype="cifs" server="library" path="GUEST_SHARE" mountpoint="~/GUEST_SHARE" options="iocharset=utf8,uid=%(USER),gid=users,dir_mode=0700,file_mode=0600" />
```

Mounts in the user's home folder. But, the folder takes on the ownership of the user logged in, and sets the UID of all the files on the share to that user.
So when user bfg looks in /home/bfg/GUEST_SHARE, all is owned by bfg
AND when user foo looks in /home/foo/GUEST_SHARE, all is owned by foo

If foo makes a new file, /home/foo/GUEST_SHARE/newfile, it is owned by foo, according to foo.  If bfg does ls /home/bfg/GUEST_SHARE, newfile is owned by bfg.

This ain't going to work.  Hmmm.  Any ideas?


Another error to fix:
On logging out, user gets....
pmvarrun(pmvarrun.c:406): could not unlink /var/run/pam_mount/bfg: Permission denied


And now for some reason, all my fstab mounts are now mounting as root, so no-one can change anything.

---

### Post by dmizer on 2009-07-03
Try adding "users" to the options, as that should allow the user to mount and unmount the volume as them self.

I'll have to do more research on the userid thing. It's difficult to push unix permissions over samba as samba wasn't designed for it.

Edit:
Depending on your NAS, I think you may need one of the following two options:

setuids
```
          If the CIFS Unix extensions  are  negotiated  with  the  server  the
          client  will  attempt  to set the effective uid and gid of the local
          process on newly created files, directories,  and  devices  (create,
          mkdir,  mknod).  If the CIFS Unix Extensions are not negotiated, for
          newly created files and directories instead of using the default uid
          and gid specified on the the mount, cache the new file&#8217;s uid and gid
          locally which means that the uid for the file can  change  when  the
          inode is reloaded (or the user remounts the share).
```
nosetuids
```
          The  client will not attempt to set the uid and gid on on newly cre&#8208;
          ated files, directories, and devices (create,  mkdir,  mknod)  which
          will  result  in  the  server setting the uid and gid to the default
          (usually the server uid of the user who mounted the share).  Letting
          the  server  (rather  than  the  client)  set the uid and gid is the
          default.If the CIFS Unix Extensions are not negotiated then the  uid
          and gid for new files will appear to be the uid (gid) of the mounter
          or the uid (gid) parameter specified on the mount.
```

---

