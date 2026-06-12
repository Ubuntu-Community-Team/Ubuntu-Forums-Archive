---
title: "getting second hard drive to work with mythtv"
date: 2013-09-17
forum: Mythbuntu
---

### Post by abduljones on 2013-09-17
My Mythbutu system is a work in progress. It generally works okay but has a few niggles. Heres one of them.
  I have my media files on a separate hard drive to the Ubuntu system. The drive can be seen when I go into my home folder and I can access and play the files from there. At present Mythtv can't see the drive and consequently can't play the files on it. The part of the drive I want Mythtv to access is dev/sdb5. I assume I've got to tell the system where to mount the hard drive at start up and then tell Mythtv where the filesare. But I don't know what the command(s) should look like. Could someone help me please?

---

### Post by wyliecoyoteuk on 2013-09-17
You can use storage groups

[http://www.mythtv.org/wiki/Storage_Groups](http://www.mythtv.org/wiki/Storage_Groups)

---

### Post by abduljones on 2013-09-18
I don't need to record to the second hard drive, I just want to play the videos that are on it through Mythbuntu, but Myth can't find them. I've read through quite a few of the articles relating to it, and have tried a few commands, but am still non the wiser how to instruct Mythbuntu to look in the other hard drive when I want to play a video.

---

### Post by Morbius1 on 2013-09-18
Please post the output of the following commands so the folks here can get some facts to work with:
```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```
```
mount
```

---

### Post by wyliecoyoteuk on 2013-09-18
You can use storage groups for videos as well:

Storage Groups

Videos in Myth can now be stored on the backend and streamed to the frontend without a NFS or Samba mount. It is critical to note that the Storage Group implementation is not complete, and to take that into consideration when weighing whether to move to Video Storage Groups.
Advantages

    Adding new frontends means zero configuration for videos, recordings, and metadata images.
    Can dynamically add space to your video library without using RAID or LVM. Loss of one drive does not mean loss of the entire library.
    Can spread video hosting across many/all backends.
    No need to set up network mounts of any kind. 

Disadvantages

    External Video Players (mplayer, xine, VLC) will not work with videos hosted on an SG.
    ISOs played back via storage group must be unencrypted.
    (0.24 and previous) The UPnP server takes its configuration from the old local video definitions. 

Setting Up Video/Image Storage Groups

    On the backend that will host the videos, stop the backend process and run mythtv-setup.
    In Storage Group configuration, set up directories for each of the following: Videos, Trailers, Fanart, Banners, Screenshots, and Coverart.
    Optional Step: If you would like to use a combination of Storage Group and locally hosted video, you can do the following. On the frontends, go to Utilities/Setup->Setup->Media Settings->Video Settings->General. Change "Directories that hold videos" to point at a directory that is not the same as the one the Storage Group points at. **Multiple entries can be entered, separated by a colon (:)**.If the local video setting and the Storage Group setting point at the same path, the video library will prefer the Storage Group path and ignore the local one.
    Enter the video library. Press the "M" (MENU) key and choose "Scan For Changes." 

Local Video Storage

If you choose not to use Storage Groups then simply don't define any of the above mentioned Storage Groups and set up your directories for videos and artwork on each individual frontend. On remote frontends the directories will need to be mounted locally via NFS or Samba. As always, the mount points need to be identical on all frontends. Then go to Utilities/Setup->Setup->Media Settings->Video Settings->General and point to the appropriate directories for Videos, Trailers, Fanart, Banners, Screenshots, and Coverart.

You can mount the disk using the disk management tool or parted, although it sounds like it is already mounted, then add extra directories.
e.g.
/var/lib/mythtv/videos:/disk2/videos:disk3/videos

---

### Post by abduljones on 2013-10-26
Thank you all for getting in touch. Sorry to be so long responding, but it's been a long and arduous first term and this has been the first chance I've had to look at the replies.

   Details requested are as follows
tracey@tracey-A780LB:~$ sudo blkid -c /dev/null
[sudo] password for tracey: 
/dev/sda1: UUID="ad717efa-aaa6-4c87-81d0-d542eee41e3a" TYPE="ext4" 
/dev/sda5: UUID="c2fcd215-9304-4fd6-86ce-4fc077441746" TYPE="swap" 
/dev/sdb5: LABEL="mediacentre" UUID="2a3d650d-fbd8-4c0b-a962-0d87a86dda2f" TYPE="ext2" 
/dev/sdb6: UUID="6c3f608c-1759-4c79-b366-20bd2795c4f4" TYPE="swap" 
tracey@tracey-A780LB:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=ad717efa-aaa6-4c87-81d0-d542eee41e3a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c2fcd215-9304-4fd6-86ce-4fc077441746 none            swap    sw              0       0
# swap was on /dev/sdb6 during installation
UUID=6c3f608c-1759-4c79-b366-20bd2795c4f4 none            swap    sw              0       0
tracey@tracey-A780LB:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/tracey/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=tracey)
tracey@tracey-A780LB:~$ 


  Will be back later today when I have done some fiddling and reminded myself where I got to

---

### Post by Morbius1 on 2013-10-26
> The part of the drive I want Mythtv to access is dev/sdb5. I assume I've  got to tell the system where to mount the hard drive at start up and  then tell Mythtv where the filesare. But I don't know what the  command(s) should look like. Could someone help me please?         
Since I don't know what mythtv is I can help you with the first part but not the second.
> /dev/sdb5: LABEL="mediacentre" UUID="2a3d650d-fbd8-4c0b-a962-0d87a86dda2f" TYPE="ext2" 
Right now when you mount the partition manually through the file manager it will mount to /media/tracy/mediacentre and will be accessible only to the user tracy regardless of the permissions on /media/tracy/mediacentre itself. So the first step is to create a mount point a level up from where it is now:
```
sudo mkdir /media/mediacentre
```
Then add a line to the end of /etc/fstab that looks like this:
```
UUID=2a3d650d-fbd8-4c0b-a962-0d87a86dda2f /media/mediacentre ext2 defaults 0 2
```
Make sure the partition is unmounted if it is currently mounted then run this command which will test for syntax errors and if there are none mount the partition to /media/mediacentre:
```
sudo mount -a
```

---

### Post by abduljones on 2013-12-29
So it's the Christmas holidays and I'm back on the case. Thank you Morbius1, my 2nd HD now mounts at switch on. I have also (through trial and error) managed to get mythtv to find all the videos on it - the pathway I needed was /media/mediacentre/videos. A few more niggles to sort out and then we'll be there. Thank you all for your help. We're sorted

---

