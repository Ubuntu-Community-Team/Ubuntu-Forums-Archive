---
title: "Can't access shared drive"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by coeus82 on 2009-05-20
Hello, 

I have a partitioned drive called "Media" and it's path is /media/disk

I set the shared settings to allow guests but for some reason I can't access it from Windows nor do I get a popup box asking for login information. Windows SEES the folder, but when I double click it it just gives me an "Access is denied" error message.

**However**, the strange thing is that the "Public" folder in /home/steve/public works! Windows can access that folder without any problems.

So there seems to be a problem with this partitioned drive in getting windows to recognize it. It was partitioned by gParted and it's fat32.

Can anyone help me get windows to recognize this drive on the network?

Here is my Samba Config file (Note: The path that's having issues is /media/disk):

```
[global]

## Browsing/Identification ###

   workgroup = HOME
   server string = %h
   wins support = yes
   wins server = 192.168.1.32
   dns proxy = no
;  name resolve order = lmhosts host wins bcast

#### Networking ####
;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = yes



#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m
   max log size = 1000
#   syslog only = no
   syslog = 0
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

security = user
username map = /etc/samba/smbusers
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user

########## Domains ###########

;   domain logons = yes
;   logon path = \\%N\profiles\%U
;   logon drive = H:
;   logon script = logon.cmd
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########
;   printing = bsd
;   printcap name = /etc/printcap
;   printing = cups
;   printcap name = cups

############ Misc ############

;   include = /home/samba/etc/smb.conf.%m
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

#   domain master = auto

;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

;   winbind enum groups = yes
;   winbind enum users = yes
;   usershare max shares = 100
   usershare allow guests = yes

#======================= Share Definitions =======================

;[homes]
;   comment = Home Directories
;   browseable = no
;   read only = yes
;   create mask = 0700

;   directory mask = 0700
;   valid users = %S

;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

;   write list = root, @lpadmin

[media]
    path = /media/disk
    public = yes
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

```

---

### Post by swerdna on 2009-05-20
The samba setup is OK regarding access permissions (at a glance). But the Linux permissions could be wrong. You will likely connect as user "nobody" and group "nobody". But the owner of the share is probably user root and group root with perhaps restricted permissions. Check to see what the Linux permissions on the mount are with this command in a console window: ```
ls -l /media | grep disk
```

If it's an automount of a fat32 disk, it could be dodgy and need to be remounted for guest access. So report the permissions and we'll see.

(Of course, it might be something entirely different.)

---

### Post by coeus82 on 2009-05-21
Here are the permissions:

```
drwx------ 4 steve root 16384 1969-12-31 19:00 disk
```

I should note that I've tried to make the permissions 744 but to no avail. Even in root I can't change the permissions. 

Note: "steve" is my username.

---

### Post by swerdna on 2009-05-21
Fat32 does not respond to chmod or chown because it's permissions and ownership are dictated solely by the mount command that mounted it (same for NTFS). The permissions "drwx------" prohibit read (and prohibit write) access by user nobody:nobody. So you have to make them to drwxrwxrwx, which is umask 0000.

If that drive is always mounted, i.e. if it's not an automounting usb drive, then you can change the mount configuration in the File Sytem Table. That's a text file called fstab, located at /etc/fstab.

You can open fstab for editing with this command: ```
gksudo gedit /etc/fstab
```

Find the line referring to the fat mount and change it to like this:
```
/dev/sdax /media/disk   vfat   users,gid=users,umask=0000,utf8=true 0 0
```sdax is an example. Replace sdax with the true location of your fat32 partition.

If this is all too hard for you. Then execute these two terminal commands and post the results back here and I'll give step by step instructions:
[LIST=1]
[*]sudo fdisk -l
[*]cat /etc/fstab
[/LIST]

Reference: [HowTo mount FAT32 (VFAT) partitions with read-write access]("http://www.swerdna.net.au/linhowtofat32.html")

---

### Post by coeus82 on 2009-05-21
Thanks,

That seemed to work. The drive is now drwxrwxrwx ... however, when I try to access it from the Windows PC, it now asks me for a login, even though I have guest enabled in the samba config file.

How do I have it open so that no login access is required. This is how my /home/steve/public currently works.

---

### Post by coeus82 on 2009-05-21
Nevermind, I got it to work. I changed gid to root and uid to my username.

One last thing, how would I change the permissions to 644 instead? Ex: If I want to make it read-only.

---

### Post by swerdna on 2009-05-21
If you want directory permissions of 644 -- how to calculate umask?
write down the chmod-style format for world-writeable directories (777) and subtract 644 to get the umask:
777
644
---
133
umask=0133 will allow to create directories with permissions drw-r--r-- and files with -rw-r--r--

---

