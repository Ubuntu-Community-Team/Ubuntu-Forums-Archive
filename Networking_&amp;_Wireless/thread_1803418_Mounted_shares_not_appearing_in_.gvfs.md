---
title: "Mounted shares not appearing in .gvfs"
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by andy.stevens on 2011-07-13
Hi,

I'm running Ubuntu 11.04 from a USB stick (with 3 Gig COW file) on an Acer Aspire One netbook.
Previously in Nautilus I connected to a Windows share on a NAS drive, was able to access the files on it no problem, even created a bookmark to it which showed up in the left hand panel.  I could see an entry for the share in ~/.gvfs, so I created a symbolic link to a subdirectory of it in my home directory which I've then been using as the storage path in Shotwell.

After rebooting from the USB yesterday, Shotwell no longer saw the files.  I've discovered that this is because the path that the link points to no longer exists - ~/.gvfs is completely empty.  At first I assumed this was just because I hadn't accessed the share so it hadn't been re-mounted.  However, after accessing the bookmark, although I can access the files just fine using Nautilus, I'm still seeing nothing in .gvfs.  I've even tried unmounting the share in Nautilus, deleting the bookmark, browsing to it in Nautilus via Network -> Windows Network -> etc. and re-creating the bookmark, but still nothing.  .gvfs remains completely empty - "ls -laF ~/.gvfs" shows only entries for . and ..
There's nothing in /etc/fstab that looks relevant (just aufs on / and tmpfs on /tmp), and /proc/mounts includes the line
gvfs-fuse-daemon /home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=999,group_id=999 0 0
so why can't I see anything in there when I've got the share open in Nautilus?  Is there some other path it might have been mounted instead?  And why should it be behaving any differently to before? I'm not aware of any updates or settings changes since it was last working okay...

Andy.

---

### Post by lacis_alfredo on 2011-07-30
Yes, same issue here.  I need other applications to 'see' the mounted directory, not just Nautilus.

Help!

Here, the remote Windows share is mounted, but the mount information is useless in decyphering where the mount point is:-

homer@TECRA:~$ mount | sort
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda1 on /boot type ext4 (rw,commit=0)
/dev/sda2 on / type ext4 (rw,errors=remount-ro,commit=0)
/dev/sda4 on /home type ext4 (rw,commit=0)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
gvfs-fuse-daemon on /home/homer/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=homer)
gvfs-fuse-daemon on /home/trunk/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=trunk)
/home/homer/.Private on /home/homer type ecryptfs (ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=1234567890123456,ecryptfs_fnek_sig=1234567890123456)
nfsd on /proc/fs/nfsd type nfsd (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
homer@TECRA:~$ 

Doing a ls -al /home/homer/.gvfs says:
ls: cannot access /home/homer/.gvfs: Transport endpoint is not connected

---

### Post by KenJean on 2011-08-02
Same problem. Anyone have any ideas?

KJ

Edit: The problem does not exist in Linux Mint 11.

---

### Post by vancouverite on 2012-01-09
Hey all, I have this same issue.  There is a bug report in launchpad, please select that the bug affects you too in order to get it addressed:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/890647](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/890647)

---

### Post by jrz on 2013-02-03
Same here, no problem until I upgraded to Mint 14. Mint Debian Edition does show the NAS shares in .gvfs and I can't find anything different in the packages installed, and I am a member of the fuse group.

---

