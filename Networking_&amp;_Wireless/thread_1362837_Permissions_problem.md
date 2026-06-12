---
title: "Permissions problem"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by RCepeda on 2009-12-23
Hello all and thank you in advance for the help.
I am running an ubuntu file server and I am running SAMBA to communicate with the rest of my network which are windows xp, vista, and 7 and they are on a workgroup. I have been trying to share some folders for about a week and sometime they work and sometimes they don't. I am having problems with some computers telling me this
 
"[\\Server\monument]("file://\\Server\monument") gen is not accessible. You might no have permissions to use this network resource. Contact the administrator of this server and find out if you have access permissions.
 
Multiple connections to a server or shared resource by the same user, using more than one user name, are no allowed. Disconnect all previous connections to the server or shared resource and try again."
 
Sometimes it gives me the option to log in, but when I put in the proper username and password it does not work.
 
BTW.... I am not new to the networking/computer world, just some what new to linux/samba/ubuntu.
 
PLEASE HELLLLLLLPPPPP!!!!

---

### Post by Morbius1 on 2009-12-23
Need more information please.

There are two ways to share files in Ubuntu - Simple ( or Nautilus ) and Classic. You didn't mention which method you're using so I'll ask you to show us the share definition for both methods. Please post the output of the following commands:

From the linux server:

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**
Type** testparm -s**

---

### Post by RCepeda on 2009-12-24
I am not all sure which on am I using(simple or classic). I will do some research on both.

randolc@server:~$ sudo net usershare info
[sudo] password for randolc: 
info_fn: file /var/lib/samba/usershares/quantum is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/monument is not a well formed usershare file.
info_fn: Error was Path is not a directory.

randolc@server:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[quantum]"
Processing section "[Employee Storage]"
Processing section "[Bidding]"
Processing section "[Finance]"
Processing section "[PRECISION]"
Processing section "[CRRLLC]"
Processing section "[MONUMENT GEN]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
    workgroup = MONEY
    server string = %h linuxserver
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
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
    valid users = avahi, backup, chrisg, daemon, ddean, klog, nobody, petert, root, seans, smbguest
    read only = No
    locking = No

[quantum]
    path = /home/ddean/storage/MONUMENT GEN/quantum
    read only = No
    guest ok = Yes

[Employee Storage]
    path = /home/ddean/storage/Employee Storage
    read only = No
    guest ok = Yes

[Bidding]
    path = /home/ddean/storage/Bidding
    valid users = avahi, petert
    read only = No

[Finance]
    path = /home/ddean/storage/Finance
    valid users = klog, petert
    read only = No

[PRECISION]
    path = /home/ddean/storage/PRECISION
    valid users = petert
    read only = No
    browseable = No
    browsable = No

[CRRLLC]
    path = /home/ddean/storage/CRRLLC
    valid users = petert
    read only = No
    browseable = No
    browsable = No

[MONUMENT GEN]
    path = /home/ddean/storage/MONUMENT GEN
    read only = No
    guest ok = Yes

---

### Post by Morbius1 on 2009-12-24
Just on a personal note, you really should get out of the Windows habit of having spaces in things. Linux hates spaces, it will work but sometimes it's awkward. So instead of "Employee Storage" for example use Cammel Back notation like EmployeeStorage or dashes like Employee-Storage.

Sorry for the rant.

(1) You might want to correct the share name warning:
> WARNING: You have some share names that are longer than 12 characters.(2) I suspect that this isn't a Samba problem because at first glance everything looks OK. I think it's a linux file permissions problem.

Let's see the ownership and permissions on those directories:
Open **Terminal **
Type **ls -l /home/ddean/storage**

Also is storage a mount point for an NTFS or vfat partition?
If it is can you post your fstab?
Open **Terminal**
Type [B]cat /etc/fstab

EDIT: [/B]You did create linux users and samba users for all those "valid" users listed in smb.conf - right?

---

### Post by Iowan on 2009-12-24
> **RCepeda said:**
> 
randolc@server:~$
info_fn: file /var/lib/samba/usershares/quantum is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/monument is not a well formed usershare file.
info_fn: Error was Path is not a directory. These would be results of the space in the sharename/path.

If that directory (*/home/ddean*)is a user's directory, it will most likely need to have permissions adjusted - or users added to ddean's group.

(Somehow, it seems like I'm just reiterating what **Morbius1** already said...)

---

### Post by RCepeda on 2009-12-28
I did not create the linux users and I don't see them in the home folder, but I did create them in Samba. I am taking over from a guy that did not document anything at all. I'm kind of flying blind for the moment.

ddean@server:~$ ls -l /home/ddean/storage
total 28
drwxrwxrwx  3 ddean ddean 4096 2009-12-17 12:03 Bidding
drwxrwxrwx  8 ddean ddean 4096 2009-12-22 15:12 CRRLLC
drwxrwxr-x  3 ddean ddean 4096 2009-10-30 10:03 DOCS
drwxrwxr-x  9 ddean ddean 4096 2009-12-15 15:53 Employee-Storage

ddean@server:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=511c724a-ea08-4eea-9b39-c1c359dcb8d3 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=87771e7f-062e-4036-8a9a-5994be4b18b3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

drwxrwxrwx  2 ddean ddean 4096 2009-12-18 11:46 Finance
drwxrwxrwx 18 ddean ddean 4096 2009-12-22 15:46 MONUMENT-GEN
drwxrwxrwx 12 ddean ddean 4096 2009-11-17 21:37 PRECISION

---

### Post by RCepeda on 2009-12-30
By the way, Why is it that if I restart the server my network does not reconnect?

---

### Post by Iowan on 2009-12-30
If the server networking is configured in */etc/networking/interfaces*, make sure there's an "auto eth0" line.

---

### Post by RCepeda on 2009-12-31
I do not find it in etc and I did a search and found a few but none that had the line "auto eth0". When I look at my desktop, on the taskbar it says auto eth0 active?!?!

---

### Post by Iowan on 2009-12-31
If your server has a desktop installed, perhaps you are using Network Manager - in which case, the connection should have a "Connect automatically" checkbox.

---

### Post by RCepeda on 2010-01-04
As a matter of fact I do. Thanks Iowan and Morbius1 for all of your help.

---

