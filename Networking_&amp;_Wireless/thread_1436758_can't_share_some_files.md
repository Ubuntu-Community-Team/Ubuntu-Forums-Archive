---
title: "can't share some files"
date: 2010-03-23
forum: Networking &amp; Wireless
---

### Post by lv. on 2010-03-23
Hey guys, I've setup sharing on ubuntu to my windows 7 PC and it recognizes folders all folders i set to share except on my partitioned 2nd hard drive. I'm thinking its because its password protected, how do i remove this security? it shows the folder but i cannot access it

On my windows 7 it gives me:
windows cannot access \\username\movies
check the spelling of the name. otherwise, there might be a problem with your network.

---

### Post by lv. on 2010-03-23
Every time I reboot and try to access my 2nd hard drive it gives me a window

[http://i152.photobucket.com/albums/s192/ilkkan69/Screenshot2.png](http://i152.photobucket.com/albums/s192/ilkkan69/Screenshot2.png)

How do I remove this so I can freely share this drive on my network?

Anyone?

---

### Post by Morbius1 on 2010-03-23
There is not enough information provided in your post to answer this question. On the surface it appears you're trying to share a folder on a partition that hasn't been mounted yet. No mount - no share. It's not password protected, it's asking for sudo password to mount the drive because only root can mount. 

So here's what we need to know:

(1) What method are you using to share your folders - there are two completely different methods. If you post the output of the following commands we can figure it out:

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**
Type **testparm -s**

(2) What filesystem exists on the second drive. If you post the output of these commands it will tell us about all your available partitions and which of those are mounted at boot:

Open **Terminal**
Type **sudo blkid -c /dev/null**
Type **cat /etc/fstab**

You really have two questions: How do I share the second drive, and how do I automount that drive so that I don't have to mount it manually. You don't have to automount to share but you at least have to manually mount before you share.

---

### Post by lv. on 2010-03-23
I think the drive is already mounted, when I right click it gives me an option to "unmount" - It gets seen by my other shared PC though I cannot cannot access the folder.

**net usershare info**
[music]
path=/home/dream/Music
comment=
usershare_acl=Everyone:R,
guest_ok=y

[movies]
path=/media/Storage/movies
comment=ubuntu
usershare_acl=Everyone:R,
guest_ok=y

[cracks]
path=/media/Storage/cracks
comment=
usershare_acl=Everyone:R,
guest_ok=y

[torrents]
path=/media/Storage/torrents
comment=
usershare_acl=Everyone:F,
guest_ok=y

**testparm -s**
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = DREAM
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

**sudo blkid -c /dev/null**
/dev/sda1: UUID="96db89aa-0419-4227-ac6d-495abaa92539" TYPE="ext4" 
/dev/sda5: UUID="5abcf6b6-d142-4616-a37a-106675403c29" TYPE="swap" 
/dev/sdb1: UUID="01CAC830B0569490" LABEL="Storage" TYPE="ntfs"


**cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=96db89aa-0419-4227-ac6d-495abaa92539 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5abcf6b6-d142-4616-a37a-106675403c29 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Morbius1 on 2010-03-24
We might be able to fix both problems at the same time. From the data you provided:
>  [COLOR=Black]/dev/sdb1[/COLOR]: UUID="01CAC830B0569490" LABEL="Storage" TYPE="ntfs"Open **Terminal**
Type **sudo umount /media/Storage**
[COLOR=Blue]*This is just in case you mounted it manually. This will unmount it.*[/COLOR]

Type **sudo mkdir [COLOR=Black]/media/Storage[/COLOR]**
[COLOR=Blue]*/media/Storage may already exist - issue the command anyway - I'm just being thorough.*[/COLOR]

Type [B]gksu gedit /etc/fstab

[/B]Copy the following line to the end of fstab:```
/dev/sdb1 /media/Storage      ntfs    defaults,nls=utf8,umask=000,uid=1000    0    0
```Save the fstab file, exit gedit, and back in the Terminal:

Type **sudo** [B]mount -a

[/B]Your current shares are already set up for that mount point so it should work without "re-sharing" them but if it doesn't simply go into Nautilus - unshare them - and then reshare them.

[I]Note to the hardcore fstab masters out there who are wondering why I'm using "umask=000" which is in the defaults and uid=1000 which is unnecessary:
umask=000 will allow access to everyone and is necessary since the shares are marked as allowing guest access. Even though it's in the defaults I like to explicitly state it so I know what I've done.
uid=1000 will make this user the owner of the mount point. This is necessary for this user to use Nautilus-share to share folders in this mountpoint.[/I]

---

