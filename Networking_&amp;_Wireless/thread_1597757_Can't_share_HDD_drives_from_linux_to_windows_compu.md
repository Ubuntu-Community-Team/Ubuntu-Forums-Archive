---
title: "Can't share HDD drives from linux to windows computer via lan"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by pimpys on 2010-10-15
Hi there,

I have serious issues with sharing the HDD drives physically on Linux machine 10.10 in my living room, with the windows 7 computer in my room, connected with wifi.

Here are some informations needed, I suppose, if not let me know what you need.

Thanks for your support as on the french forum I can't find any resolutions,

Regards,


/etc/samba/smb.conf 
  
> [MP3]
          path = /media/MP3
          writeable = yes
          browseable = yes
          guest ok = yes
  [Datas]
          path = /media/Datas
          writeable = yes
          browseable = yes
          guest ok = yes
   
  [Videos]
          path = /media/Videos
          writeable = yes
          browseable = yes
          guest ok = yes
   
  [Music2]
          path = /media/Music2
          writeable = yes
          browseable = yes
          guest ok = yesls -l /media

> pimpy@pimpytux:~$ sudo ls -l /media
total 32
drwxrwxrwx 1 root  root   8192 2010-05-22 20:38 Datas
lrwxrwxrwx 1 root  root      7 2010-10-13 13:24 floppy -> floppy0
drwxr-xr-x 2 root  root   4096 2010-10-13 13:24 floppy0
drwxrwxrwx 1 root  root  12288 2010-05-22 18:02 MP3
drwxrwxrwx 6 pimpy pimpy  4096 2010-05-22 20:32 Music2
drwxrwxrwx 4 pimpy pimpy  4096 2010-06-15 20:09 VideosBlkid

> pimpy@pimpytux:~$ sudo blkid

/dev/sda1: LABEL="MP3" UUID="445CB40F5CB3F9AE" TYPE="ntfs"
/dev/sda2: LABEL="Music2" UUID="689882b0-e076-47b3-975d-2a25b0917fc0" TYPE="ext4"
/dev/sdb1: UUID="903fb380-2d89-4b48-b3d2-975a684b6044" TYPE="ext4"
/dev/sdb2: LABEL="Videos" UUID="36134f53-9f52-4b41-8ff6-ee3ebb3d42ce" TYPE="ext4"
/dev/sdc1: LABEL="Datas" UUID="C828B74B28B736F2" TYPE="ntfs"FSTAB :


> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc    /proc   proc    nodev,noexec,nosuid     0       0

#Entry for /dev/sdb1 :
UUID=903fb380-2d89-4b48-b3d2-975a684b6044       /       ext4    errors=remount-ro       0       1
#Entry for /dev/sdc1 :
UUID=C828B74B28B736F2   /media/Datas    ntfs-3g defaults,locale=fr_CH.UTF-8     0       0
#Entry for /dev/sda1 :
UUID=445CB40F5CB3F9AE   /media/MP3      ntfs-3g defaults,nosuid,nodev,locale=fr_CH.UTF-8        0$
#Entry for /dev/sda2 :
UUID=689882b0-e076-47b3-975d-2a25b0917fc0       /media/Music2 ext4 defaults 0 0
#Enrty for /dev/sdb2 :
UUID=36134f53-9f52-4b41-8ff6-ee3ebb3d42ce        /media/Videos ext4 defaults 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8        0       0
/dev/scd0       /media/cdrom0 udf,iso9660 user,noauto,exec,utf8         0       0And testparm :

> pimpy@pimpytux:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[MP3]"
Processing section "[Datas]"
Processing section "[Videos]"
Processing section "[Music2]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
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

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[MP3]
    path = /media/MP3
    read only = No
    guest ok = Yes

[Datas]
    path = /media/Datas
    read only = No
    guest ok = Yes

[Videos]
    path = /media/Videos
    read only = No
    guest ok = Yes

[Music2]
    path = /media/Music2
    read only = No
    guest ok = Yes

---

### Post by pimpys on 2010-10-16
This is solved,

Thanks granade ! for this message [http://ubuntuforums.org/showthread.php?t=1596947](http://ubuntuforums.org/showthread.php?t=1596947)

> **granade said:**
> Thank you both for you responses!


I have resolved the problem...


WIN 7 is the issue!


If you follow the steps below it should work for you:

[B]Control Panel - Administrative Tools - Local Security Policy

Local Policies - Security Options



Network security: LAN Manager authentication level
Send LM & NTLM responses

Minimum session security for NTLM SSP (there are 2 of these-disable both)
Disable Require 128-bit encryption[/B]


I was able to connect to the shares once i changed the above settings. 

:guitar:

---

