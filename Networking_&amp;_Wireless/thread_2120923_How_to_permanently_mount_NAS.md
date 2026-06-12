---
title: "How to permanently mount NAS?"
date: 2013-02-27
forum: Networking &amp; Wireless
---

### Post by mark2741 on 2013-02-27
I recently purchased a WD My Book Live NAS. Nautilus can see it just fine by simply clicking on Network. 

I have on the NAS a directory named "Media" that has various subdirectories such as Music, TV Shows, Moves, etc.

I want to make these directories available to a media server that is installed on my Ubuntu 12.10 64-bit machine. I've tried both Plex (my preference) and XBMC and both of them cannot browse/see the NAS by default.

I am 99% sure that I need to setup a symbolic link of some sort via /etc/fstab, but I could be wrong.

Here is the info about my NAS:

IP to the NAS: 192.168.1.5
The NAS is formatted as ext4 by the factory.
On the NAS is a parent directory named "Network_Storage" and in there are the various subdirectories, including the "Media" one.

There is no user id/pw required to access the NAS. "Anonymous" access is enabled.

To make it so that Plex could see the NAS, I tried the following:

1. as sudo, created the directory: /media/Network_Storage
2. Changed /media/Network_Storage directory permissions to 777
3. Added the following to /etc/fstab as sudo:
#Entry for WD NAS Media
//192.168.1.5/share /media/Network_Storage cifs guest,_netdev 0 0

(I also tried starting it with "//192.168.1.5/Network_Storage and still no luck).

No luck. Plex still doesn't see it. It's not just Plex - if I navigate to /media/Network_Storage there is nothing in it.

What am I doing wrong?

---

### Post by joeashcraft on 2013-02-27
Connect to it using Nautilus, then look in "/etc/mtab" to see what was mounted and how. I suspect it's being mounted via "gvfs". [Look around for "auto mount gvfs"]("http://askubuntu.com/questions/56428/how-to-automount-a-gvfs-file-system-on-logon").

/etc/mtab shows currently mounted filesystems
/etc/fstab shows filesystems to mount on boot or filesystems to "remember"

---

### Post by mark2741 on 2013-02-27
I believe this is the entry for the NAS:

/dev/sda3 / ext4 rw,errors=remount-ro 0 0

I checked with the manufacturer of the NAS (Western Digital) and they say it is an ext4 formatted drive.

---

### Post by joeashcraft on 2013-02-27
/etc/mtab is formatted just like /etc/fstab...

so in ```
/dev/sda3 / ext4 rw,errors=remount-ro 0 0
```

_/dev/sda3_ is the device
_/_ is the mount point
_ext4_ is the filesystem type

This is not your NAS because the NAS isn't mounted at "/" (root).

If the NAS is still connected in Nautilus, then see if there's anything in _~/.gvfs_. If your NAS is listed there, then gvfs is handling the mount. See the link in my previous post about automounting gvfs things.

---

### Post by mark2741 on 2013-02-27
Joe,

Thanks for your help so far. I'm confused/unsure though - where/how do I look for ~/.gvfs?

With the NAS viewable in Nautilus, here are the complete contents of /etc/mtab:

/dev/sda3 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0
/dev/sda1 /media/System_Reserved fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfsd-fuse /run/user/mark/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=mark 0 0
gvfsd-fuse /root/.gvfs fuse.gvfsd-fuse rw,nosuid,nodev 0 0
/dev/sda3 /media/NETWORK_STORAGE ext4 rw,errors=remount-ro 0 0

---

### Post by joeashcraft on 2013-02-27
> **mark2741 said:**
> I'm confused/unsure though - where/how do I look for ~/.gvfs?

In linux, _~/_ is a user's home directory (usually /home/_username_/). _~bob/_ would go to bob's home directory, and _~/_ always goes to the home directory of the current user.

So, _~/.gvfs/_ is probably _/home/mark/.gvfs/_.

> **mark2741 said:**
> gvfsd-fuse /run/user/mark/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=mark 0 0
gvfsd-fuse /root/.gvfs fuse.gvfsd-fuse rw,nosuid,nodev 0 0

This is the part I was looking for. This confirms that you are using [GVFS]("http://en.wikipedia.org/wiki/GVFS"). Now you just need to look in _~/.gvfs_ to make sure your NAS is there.

If your NAS *is* listed in _~/.gvfs_, then _[search for "auto mount gvfs"]("http://askubuntu.com/questions/56428/how-to-automount-a-gvfs-file-system-on-logon")_.

---

### Post by mark2741 on 2013-02-28
I'm looking in my home directory, via Nautilus with "Show Hidden Files" enabled, and there is no .gvfs directory. Also did a search with no results.

---

### Post by joeashcraft on 2013-02-28
Try [this command]("http://www.unix.com/man-page/OpenSolaris/1/gvfs-mount/"):
```
gvfs-mount -l
```
This will show you everything that GVFS has mounted. If your NAS is listed, then GVFS is handling the NAS.

---

### Post by mark2741 on 2013-02-28
This is the output of gvfs-mount -l:

mark@mark-linux:~$ gvfs-mount -li
Mount(0): Media for anonymous on Network-Storage- -> afp://anonymous@Network-Storage.local/Media/
  Type: GDaemonMount
  default_location=afp://anonymous@Network-Storage.local/Media/
  themed icons:  [folder-remote-afp]  [folder-remote]  [folder]
  symbolic themed icons:  [folder-remote-symbolic]  [folder-remote]  [folder]
  can_unmount=1
  can_eject=0
  is_shadowed=0
Mount(1): Documents for anonymous on Network-Storage- -> afp://anonymous@Network-Storage.local/Documents/
  Type: GDaemonMount
  default_location=afp://anonymous@Network-Storage.local/Documents/
  themed icons:  [folder-remote-afp]  [folder-remote]  [folder]
  symbolic themed icons:  [folder-remote-symbolic]  [folder-remote]  [folder]
  can_unmount=1
  can_eject=0
  is_shadowed=0
Mount(2): Mark on Network-Storage- -> afp://Network-Storage.local/Mark/
  Type: GDaemonMount
  default_location=afp://Network-Storage.local/Mark/
  themed icons:  [folder-remote-afp]  [folder-remote]  [folder]
  symbolic themed icons:  [folder-remote-symbolic]  [folder-remote]  [folder]
  can_unmount=1
  can_eject=0
  is_shadowed=0


I can't seem to get the root directory (in Windows parlance, the "C:" level) to mount - I have to open up one of the directories on the NAS before anything shows up in gvfs. That's fine though. I can see my "Media", "Mark", and "Documents" directories above.

Now the question is: since they are NOT in a ~/.gvfs directory (there is none on my system), then how do I symbolically link to them? The reason I need them to auto-mount and symbolically link to them is because I need the Plex Media Server to be able to access the Media directory's contents. When I did this before (with an NTFS drive, I did it by setting up a /media/Network_Share directory and then a symbolic link to that directory from the NTFS drive. Then I was able to set permissions on the /media/Network_Share directory so that Plex could access the NTFS stuff.

---

### Post by LewisTM on 2013-02-28
A few pointers:

1) In 12.10, the gvfs directory is in /run/user/<you>/gvfs _not_ ~/.gvfs
Hence the line 
> gvfsd-fuse /run/user/mark/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=mark 0 0
from the [FONT=Courier New]mount[/FONT] command

2) Symbolic links are files, they are not fstab entries. Those are two separate things. You can either setup an fstab entry to mount the share at boot or place a symbolic link somewhere on your file system that points to the appropriate /run/user/<you>/gvfs/<share> location. That location **must** be mounted. A good way to do it is to execute at login
```
gvfs-mount smb://anonymous@Network-Storage.local/Mark
```
The following directory should be created by gvfsd: /run/user/mark/gvfs/smb-share:server=Network-Storage.local,share=Mark
So you can make a symlink to it like this:
```
sudo ln -s "/run/user/mark/gvfs/smb-share:server=Network-Storage.local,share=Mark" /media/Network_Storage/Mark
```
The directory /media/Network_Storage/Mark must _not_ exist beforehand.
Repeat for the other shares.
You can also use this info to setup a cifs share in fstab. Something like
```
//Network-Storage.local/Mark /Network_Storage/Mark cifs guest,_netdev 0 0
```
In this case, the directory .../Mark _must_ exist

3) You should consider accessing your NAS through NFS (I think it [supports]("http://community.wdc.com/t5/Network-Product-Ideas/NFS-Support-for-MyBookLive/idi-p/148160") it). It's faster and supports true Linux-type file permissions.
Install package nfs-common
The fstab entry for a share would be something like
```
Network-Storage.local:/Mark /Network_Storage/Mark nfs user,rsize=8192,wsize=8192,timeo=14,intr 0 0
```

Cheers!

---

