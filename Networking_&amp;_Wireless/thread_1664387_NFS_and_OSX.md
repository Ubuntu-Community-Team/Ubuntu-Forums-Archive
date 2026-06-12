---
title: "NFS and OSX"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by TangRedSocks on 2011-01-10
I have read this about a million times: [http://nfs.sourceforge.net/nfs-howto/ar01s03.html](http://nfs.sourceforge.net/nfs-howto/ar01s03.html) .
I have tried to set it up exactly as shown. 

I want to share a mount "/RAID" on my server: 192.168.0.2 with everyone on my network.192.168.0.*
From what I have listed below I am able to mount the share but I can not write or delete anything. It is almost like it is ro only permissions.

From the Server:
```
sudo cat /etc/exports
[sudo] password for jesse: 
# /etc/exports: the access control list for filesystems which may be exported
#        to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/RAID 192.168.0.0/255.255.255.0(rw,insecure,no_root_squash,async,no_subtree_check)


rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  54496  status
    100024    1   tcp  51715  status
    100021    1   udp  37376  nlockmgr
    100021    3   udp  37376  nlockmgr
    100021    4   udp  37376  nlockmgr
    100021    1   tcp  38757  nlockmgr
    100021    3   tcp  38757  nlockmgr
    100021    4   tcp  38757  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100227    2   tcp   2049
    100227    3   tcp   2049
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100227    2   udp   2049
    100227    3   udp   2049
    100005    1   udp  32971  mountd
    100005    1   tcp  50982  mountd
    100005    2   udp  32971  mountd
    100005    2   tcp  50982  mountd
    100005    3   udp  32971  mountd
    100005    3   tcp  50982  mountd

sudo mount -l
/dev/sdg5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw,relatime)
/dev/md0p1 on /RAID type ext4 (rw,noexec,commit=0)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
```On my client machine:
```
rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  53723  status
    100024    1   tcp  41699  status

mount -l
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda1 on /media/SYSTEM type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions) [SYSTEM]
192.168.0.2:/RAID on /RAID type nfs (rw,vers=4,addr=192.168.0.2,clientaddr=192.168.0.147)

```Eventually I need to share 192.168.0.2:/RAID on two OSX computers as well. I read some places where you need to add insecure to your /etc/exports on your server in order for the OSX client to access the the share. 

Any help would be appreciated as this is suppose to be the easy route vs smb.

---

### Post by TangRedSocks on 2011-01-17
Most the issues have been solved. To sum up it was (I think) folder/file ownership restrictions. After installing smb and changing rw attribute to nobody/nogroup both smb and nfs seem to be working.

---

