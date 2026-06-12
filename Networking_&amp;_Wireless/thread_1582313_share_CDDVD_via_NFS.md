---
title: "share CD/DVD via NFS?"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by Hawkoon on 2010-09-26
Hi All,

I would like to access the CD/DVD drive of my 8.04 Ubuntu server from my EeePC. I have already exported a couple of folders via NFS and it is all working fine, but for the CD drive it is just not working.

I export the drive in /etc/exports with

```
/cdrom 192.100.100.2(ro)
```and checking with

```
showmount -e
```I get

```
/media/cdrom0 192.100.100.2
```When I now mount /media/cdrom0 I just get an empty folder rather than seeing the content of the CD in the drive. Actually, I cant even find the CD mount point on the server. The CD is auto-mounted and shows up as "Audio Disc" on the desktop, but /media/cdrom, /media/cdrom0 and /cdrom are also all empty. Checking the mounts with mount -l doesnt give me any clue where the CD is mounted to:

```
/dev/sda10 on / type ext3 (rw,relatime,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
/dev/sda11 on /home type ext3 (rw,relatime) []
securityfs on /sys/kernel/security type securityfs (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
gvfs-fuse-daemon on /home/hartmut/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hartmut)
```I found one thread on NFS sharing a CD drive [HTML]http://www.networkedmediatank.com/showthread.php?tid=6498[/HTML] but I am not sure what to do when it says under point 4 "mount dvdreadfs".

Anyone knows a solution to get network access to the drive?

---

### Post by Hawkoon on 2010-09-29
OK, I found a way to access my server DVD drive via NFS, although it is not a very comfortable approach beause I cannot just stick in a new CD and see it right away from my client. Reason is that mounting doesn't work on the drive level but on the CD level. If someone knows a more elegant approach I am all ears :D

Anyway, here is how I access my DVD drive via NFS:

1) find out DVD drive device location with ```
> sudo lshw
``` in my case it is located at /dev/sr0

2) mount the drive (read-only) on the server ```
> sudo mount -r /dev/sr0 /mountpoint_on_server
``` This only seems to work for data discs, and NOT for audio discs

3) export mountpoint_on_server in /etc/exports with ```
/mountpoint_on_server client_IP(ro)
```

4) start/restart nfs server ```
> sudo /etc/init.d/nfs-kernel-server restart
```

5) mount nfs export on client side ```
> sudo mount -r server_IP:/mountpoint_on_server /mountpoint_on_client
```

After this last step the CD is accessible from the client in /mountpoint_on_client. If I want to access a different CD I have to first unmount on the client side, then on the server side and then stop the nfs server (otherwise mountpoint_on_server will be deleted). With the new CD in the drive I have to apply steps 2, 4 and 5 again. Quite a headache, but it is working. If I find a more elegant approach I will post it here.

---

