---
title: "NFS server shares will not mount"
date: 2013-02-16
forum: Networking &amp; Wireless
---

### Post by cscj01 on 2013-02-16
I set up an NFS home network using the instructions shown here: > [http://ubuntuforums.org/newthread.php?do=newthread&f=336]("http://ubuntuforums.org/newthread.php?do=newthread&f=336")The system worked perfectly until I had to reboot the server.  At that point I could no longer get the NFS shares on the server to mount.  The folders are all present, the exports work properly, the share shows on the client, but there are no files in the client mount location.

When I try to manually mount the server share, I get a message saying > No such directory or fileHowever, the directory does exist.

I have checked each step in the instructions with what I have in my files:[LIST=1]
[*]/etc/fstab;
[*]/etc/default/nfs-kernel-server;
[*]/etc/default/nfs-common;
[*]/etc/exports;
[*]/etc/idmapd.conf
[/LIST]on the server and appropriate files on the client.  They all seem to be correct.

The strange thing to me is these worked before the reboot.  Any ideas would be appreciated.

---

### Post by cscj01 on 2013-02-16
Here's my configuration info.

From the NFS Server:

/etc/fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
# / was on /dev/sda5 during installation
UUID=a00cc678-008c-496a-9fc6-213250ba5b6b /  ext4   errors=remount-ro 0  1
# swap was on /dev/sda6 during installation
UUID=a471427e-e168-46b3-8108-c183c3c4fd38 none   swap  sw   0   0
/dev/fd0   /media/floppy0   auto   rw,user,noauto,exec,utf8  0  0
# CP1 Data Drive Backup share
/media/Ubuntu_Data_Backup  /export/cp1databackup  none   bind  0  0/etc/exports
> # /etc/exports: the access control list for filesystems which may be exported
#                     to NFS clients.   See exports(5).
#
# Examples for NFSv2 and NFSv3:
# /srv/homes         hostname1(rw,sync,fsid=0,crossmnt,no_subtree_check)
#
# Example for NFSv4:
# /srv/nffs4     gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nts4/homes  gss/krb5i(rw,sync,no_subtree_check)
# Exports for CP1 Data Backups
/export      192.168.1.0/24(rw,fsid=0,insecure,no_subtree_check,async)
/export/cp1databackup   192.168.1.0/24(rw,nohide,insecure,no_subtree_check,async)
/etc/idmapd.conf
> [General]

Verbosity = 0
Pipefs-Directory = /run/rpc_pipefs
# set your own domain here, if id differs from FQDN minus hostname
# Domain = localdomain

[Mapping]

Nobody-User = nobody
Nobody-Group = nogroup

/etc/default/nfs-common
> # If you do not set values for the NEED_ options, they will be attempted
# autodetected; this should be sufficient for most people. Valid alternatives
# for the NEED_ options are "yes" and "no".

# Do you want to start the statd daemon? It is not needed for NFSv4.
NEED_STATD=

# Options for rpc.statd.
#   Should rpc.statd listen on a specific port? This is especially useful
#   when you have a port-based firewall. To use a fixed port, set this
#   this variable to a statd argument like: "--port 4000 --outgoing-port 4001".
#   For more information, see rpc.statd(8) or [http://wiki.debian.org/SecuringNFS](http://wiki.debian.org/SecuringNFS)
STATDOPTS=

# Do you want to start the gssd daemon? It is required for Kerberos mounts.
NEED_IDMAPD=yes
NEED_GSSD=no # no is the default

/etc/default/nfs-kernel-server
> # Number of servers to start up
# To disable nfsv4 on the server, specify '--no-nfs-version 4' here
RPCNFSDCOUNT=0

# Options for rpc.mountd
# If you have a port-based firewall, you might want to set up
# a fixed port here using the --port option.  For more information,
# see rpc.mountd(8) or [http://wiki.debian.org/SecuringNFS](http://wiki.debian.org/SecuringNFS)
# To disable NFSv4 on the server, specify '--no-nfs-version 4' here
RPCMOUNTDOPTS=--managegids

# Do you want to start the svcgssd daemon? It is only required for Kerberos
# exports. Valid alternatives are "yes" and "no"; the default is "no".
NEED_SVCGSSD=no # no is the default

# Options for rpc.svcgssd.
RPCSVGSSDOPTS=

# Options for rpc.nfsd.
RPCNFSDOPTS=

```
showmount -e cp2
Export list for cp2:
/export/cp1databackup 192.168.1.0/24
/export               192.168.1.0/24
``````
sudo mount --bind /media/Ubuntu_Data_Backup /export/cp1databackup
mount: No such file or directory
```

From the NFS Client:

/etc/fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdb1 :
UUID=00AE2EA54F4183A2	/media/Data	ntfs-3g	defaults,nosuid,nodev,locale=en_US.UTF-8	0	0
#Entry for /dev/sda1 :
/dev/sda1	/media/sda1	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for Samba Share drive g on cp2
#//cp2/g	/mnt/cp2	smbfs	iocharset=utf8,uid=1000	0	0

#Entry for NFS Server on drive g on cp2
cp2.local:/   /mnt   nfs4    _netdev,auto  0  0

/etc/idmapd.conf
> [General]

Verbosity = 0
Pipefs-Directory = /run/rpc_pipefs
# set your own domain here, if id differs from FQDN minus hostname
# Domain = localdomain

[Mapping]

Nobody-User = nobody
Nobody-Group = nogroup

/etc/default/nfs-common
> # If you do not set values for the NEED_ options, they will be attempted
# autodetected; this should be sufficient for most people. Valid alternatives
# for the NEED_ options are "yes" and "no".

# Do you want to start the statd daemon? It is not needed for NFSv4.
NEED_STATD=

# Options for rpc.statd.
#   Should rpc.statd listen on a specific port? This is especially useful
#   when you have a port-based firewall. To use a fixed port, set this
#   this variable to a statd argument like: "--port 4000 --outgoing-port 4001".
#   For more information, see rpc.statd(8) or [http://wiki.debian.org/SecuringNFS](http://wiki.debian.org/SecuringNFS)
STATDOPTS=

# Do you want to start the gssd daemon? It is required for Kerberos mounts.
NEED_IDMAPD=yes
NEED_GSSD=no # no is the default

```
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdc2       421G  176G  224G  44% /
udev            2.9G  4.0K  2.9G   1% /dev
tmpfs           1.2G  1.1M  1.2G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.9G  204K  2.9G   1% /run/shm
/dev/sdb1       1.4T  873G  525G  63% /media/Data
/dev/sda1        31G   23G  8.0G  75% /media/sda1
cp2.local:       47G  4.1G   41G  10% /mnt
/dev/sdc1        31G   20G   12G  64% /media/C48C88E98C88D6F8_
/dev/sdc2       421G   89G  311G  23% /media/b61632e9-7186-4ec9-9e4c-214c01d39a4e

```

---

### Post by papibe on 2013-02-16
Hi cscj01.

Could you post the actual mount command you are running, and the actual error message?

Regards.

---

### Post by cscj01 on 2013-02-16
```
sudo mount --bind /media/Ubuntu_Data_Backup /export/cp1databackup
mount: No such file or directory
```This is on the server side.  I have it in fstab as well to automatically mount```
/media/Ubuntu_Data_Backup /export/cp1databackup none bind 0 0 
```biut it won't work that way either.

---

### Post by cscj01 on 2013-02-17
Okay, I have found a few interesting things that may or may not be problems.  So let me describe my current environment and what I would like to accomplish.

I have two PC's, both of which are currently using Ubuntu 12.04; one is x64 and the other x32.  I'll refer to them respectively as CP1 and CP2.

CP1 is what I use for my work which includes finances, photography, and music (digitizing of analog media, primarily LPs and tapes).  I have Ubuntu on one internal hard drive (I'll call it my system drive), and all of my data on a separate internal hard drive (I'll call it my data drive).  I have one external USB drive I use to occasionally clone my system drive using Clonezilla.  I have a dual boot set up on the system drive with XP SP3, but I recently installed Virtualbox and created an XP VM.  I plan to get rid of the separate XP partition when I get all the XP software I need working in the VM.

CP2 is my wife's computer, and her use is a bit more casual than mine.  Her requirements are mainly for Firefox, image viewing, and Libreoffice applications.  I have two internal hard drives, one being the system drive and one being the data drive in the sense of CP1.  I have two USB external hard drives attached to CP2.  One is used to clone the CP2 system drive, and the other is used to backup the data drive of CP1.  I run luckyBackup on CP1 to accomplish the backup of the data drive on CP1 to the external USB hard drive on CP2.  I also have a dual boot on CP2, and have recently moved my wife to Ubuntu.

Before, when CP2 was only XP, I used Samba to share the USB external hard drive on CP2 with CP1.  That allowed me to mount the USB drive on CP1 in order to run luckyBackup.  After installing Ubuntu on CP2, I decided to create an NFS Home Network rather than Samba.  That setup has CP2 as the server and CP1 as the client.  I have included my current files and a couple of command results for the two systems in a post above.

While struggling with the problems that began after I had to reboot the server (CP2), some odd things (at least to me) have come to light.  The first concerns directory ownership and permissions.  ON CP2, I created two directories to export my backup USB drive so I could have it mounted as an NFS share on CP1 to execute luckyBackup.  I called these /export and /export/cp1databackup.  The owner was root and they both had 777 permissions.  However, when I reboot CP2, cp1databackup has my wife as owner, and only she has access.  Group and Others have no access.  I then have access problems on CP1 when I try to access the mounted CP2 share on CP1.  I included a mount in /etc/fstab as seen in the post above.

The second problem seems to occur randomly.  If I mount the CP2 share on CP1, it will sometimes disappear.  By this I mean if I browse to the location on CP1 which is /mnt/cp1databackup, I show no files.  However, those files were there after I mounted cp2.local as indicated in the post above.  And if I come back some time later, they may show again when I browse to /mnt/cp1databackup.

A third problem presents itself this way.  If I mount the CP2 share on CP1, on some occasions when I browse to /mnt/cp1databackup, Nautilus goes into a busy state and will not end.  If I use Systems Monitor to check it, Nautilus shows as Uninterruptible.  I have found no way to kill the process, either from Systems Monitor or from a terminal as super user.  I am forced to restart CP1.

Finally, a fourth issue is trying to unmount the mounted share.  If I use sudo umount, I am told the resource is busy.  If I try umount.nfs, I am told the mounted system is not an NFS file system.

So I have so many issues happening, I cannot sort things out.  Is mounting a share that is on an external USB drive a problem within itself?  Why can I not unmount the share?  Why does the share disappear at times.  Why does Nautilus go into a state that does not allow me to kill the process?  Why am I told the share is not an NFS system when it was mounted as one?

Hopefully, someone can sort out some of these issues because I am just trying my first NFS configuration.  Any suggestions/answers will be most appreciated.

---

### Post by SeijiSensei on 2013-02-17
> **cscj01 said:**
> ```
sudo mount --bind /media/Ubuntu_Data_Backup /export/cp1databackup
mount: No such file or directory
```This is on the server side.  I have it in fstab as well to automatically mount```
/media/Ubuntu_Data_Backup /export/cp1databackup none bind 0 0 
```biut it won't work that way either.

On the client you should be using something like :

```
sudo mount servername:/media/Ubuntu_Data_Backup /export/cpidatabackup
```

Your command doesn't specify a server name.  I've never used the --bind option with NFS mounts either.  

I export a mounted USB external drive just fine.  You have to make sure you export any subdirectories individually.  Suppose the external is mounted as /media/external on the server.  Exporting /mount will not automatically export /media/external as well for security reasons.  You would need separate entries for /media and /media/external in the server's /etc/exports file.  Also try adding "insecure" to the list of server options for this share.  It's not really all that "insecure" and it might help.

On the server, open a terminal and run "sudo tail -f /var/log/syslog" then try to connect from the client.  What does the log show?

---

### Post by cscj01 on 2013-02-17
> **SeijiSensei said:**
> On the client you should be using something like :

```
sudo mount servername:/media/Ubuntu_Data_Backup /export/cpidatabackup
```
For the client side, I use```
sudo mount -t nfs4 -o proto=tcp,port=2049 cp2.local:/ /mnt
```Should I be using /mnt/cp1databackup instead?

---

### Post by cscj01 on 2013-02-17
Mounting is no longer a problem.  I am closing this thread and opening a new thread under General because of the other issues.

---

