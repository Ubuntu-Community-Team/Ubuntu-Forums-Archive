---
title: "samba not sharing between teo ubuntu machines"
date: 2010-08-06
forum: Networking &amp; Wireless
---

### Post by badbradmx on 2010-08-06
probably missed something really small but ive got an old celeron 2.4GHz laptop with a busted inverter and no VGA output (it too is broke.....off) and ive decided to use it as a file and maybe print server.
the folders i want to share are on an external drive so i added the line

usershare owner only = false

to the global section in the smb.conf file yet it wont share the folders. im fairy new to linux so simple steps are much appreciated.

both are using lucid

PS how to you do the code boxes?
PSS if you wanna know how i can see the screen just ask

---

### Post by sikander3786 on 2010-08-06
Hi.

What happens when you share a folder from nautilus? Is there any error message?

Please post of output of "testparm" from terminal.

Regards.

---

### Post by badbradmx on 2010-08-06
The error message i get when trying to access the files is 

unable to mount location - failed to mount windows share

could it be because the server is dual booting?

and heres the testparm

server@server-laptop:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
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
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

---

### Post by sikander3786 on 2010-08-06
How did you share the folders on the server? There are no shares defined in your smb.conf, did you use nautilus to share the folders?

What is the output of

*net usershare info*

*sudo net usershare info*

---

### Post by badbradmx on 2010-08-06
well i went into the folder i wanted to share then right clicked and went into the sharing options and created it that way. i can share files on the home directory, on the internal drive.

maybe i need to update something, i only just installed the OS on the laptop today

--updated and here is the output (the freeagent shares are on the external) i "borrowed" the sample pictures from the windows partition to test the internal drive sharing, which works as i think i said above

server@server-laptop:~$ net usershare info
[pictures]
path=/media/FreeAgent Disk/Files/Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=y

[sample pictures]
path=/home/server/Pictures/Sample Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=y

[music]
path=/media/FreeAgent Disk/Files/Music
comment=
usershare_acl=Everyone:F,
guest_ok=y

---

### Post by sikander3786 on 2010-08-06
I think this a problem with the ownership and permissions. Who is the owner of the files on the external HDD? If it is you then I think some wiser heads than mine will have to jump in :-(

---

### Post by badbradmx on 2010-08-06
i think the laptop i wanna access it from owns them but that's what the line of code was for, so that samba could share files that arent owned. whats the code to change the ownership, chown or something lol

---

### Post by Morbius1 on 2010-08-06
> path=/media/FreeAgent Disk/Files/Pictures
path=/media/FreeAgent Disk/Files/Music(1) Is the "FreeAgent Disk" formatted in ntfs of FAT32 by any chance?

(2) Please post the output of the following command so we can see the permissions:

```
ls -al /media/"FreeAgent Disk"
```

---

### Post by badbradmx on 2010-08-06
does the format matter? linux can read windows formats anyway cant it? i believe its ntfs and here is the output
server@server-laptop:~$ ls -al /media/"FreeAgent Disk"
total 217
drwx------ 1 server server   4096 2010-08-06 10:30 .
drwxr-xr-x 4 root   root     4096 2010-08-06 16:02 ..
-rwxrwxrwx 1 server server     67 2010-07-08 10:50 Autorun.inf
drwx------ 1 server server   4096 2010-08-06 12:53 Files
-rwxrwxrwx 2 server server  44902 2009-04-16 17:13 FreeAgentDesktopNext.ico
-rwxrwxrwx 1 server server     51 2010-07-15 00:27 .is_audio_player
drwx------ 1 server server      0 2010-07-09 16:36 $RECYCLE.BIN
drwx------ 1 server server      0 2009-05-02 01:23 Seagate
drwx------ 1 server server      0 2010-07-08 10:50 Seagate Backup
-rwxrwxrwx 1 server server 156312 2009-01-17 00:14 Setup.exe
drwx------ 1 server server      0 2010-07-12 19:10 Subs.2.3
drwx------ 1 server server   4096 2010-07-08 10:42 System Volume Information

---

### Post by Morbius1 on 2010-08-06
It matters how it's formatted because of this:
>  drwx------ 1 server server   4096 2010-08-06 12:53 FilesThere is only one user that can access that folder regardless of what samba is allowing and that's "server".

If it were formatted in say ext3 then you could correct it by using a chmod 777. But chmod doesn't work on a windows filesystem.

The easy way out of this without resorting to fstab is to do the following:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add a line to the [global] section of smb.conf:
```
force user = server
```Save the file, exit gedit, and back in the terminal restart samba:
If you're using Ubuntu 10.04:
```
sudo service smbd restart
```If you're using an earlier version:
```
sudo service samba restart
```Force user will act as a mask and convert your remote user to server for all your shares.

---

### Post by badbradmx on 2010-08-06
that appears to have worked thank you so much, now i will be asking soon if i cant get my windows PC's to connect and maybe on the security front.

but to fix i uninstalled samba and reinstalled it just to make sure. reconfigured the smb.conf file as above (which was in a different directory, no idea why) and now its streaming like a charm.

thank you so much once again for all your help, much appreciated

---

