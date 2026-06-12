---
title: "Need Help sharing a Folder/Drive"
date: 2011-09-29
forum: Networking &amp; Wireless
---

### Post by Mr.BadExample on 2011-09-29
Good Afternoon everyone,

I've recently taken the plunge and have gone 100% linux via Ubuntu. Love what's going on so far except for a few minor issues. Which I'll ask here.

I have a 2 Hard Drives on my Machine, the main drive has my Ubuntu install and all the partitions for that. I recently partitioned out the 2nd drive to use as a backup device for the other PC's on the Network. I partitioned it as NTFS feeling that was the most logical step since the other PC's are Window's based.

I configured personal file sharing to share the drive, but no one can access it. It shows on the network but others are getting access denied. The public folder on the main drive shares fine as well as the printer.

---

### Post by Morbius1 on 2011-09-29
Somewhat confusing post.

If you're trying to share the NTFS partition then Personal FIle Sharing is not the right tool since It will only share one folder on your entire system:
/home/your-user-name/Public.

I'm kind of surprised that it shows up at all on the Windows machines since that doesn't work very well.

Are you sure you didn't right click a folder in Nautilus and select "Sharing Options" instead?

---

### Post by azmyth on 2011-09-29
If you're sharing with Windows, you'll want to use samba. Is it WinXP or Vista or 7? With XP, you need to create a samba user to match the XP login credentials.

---

### Post by Morbius1 on 2011-09-29
> With XP, you need to create a samba user to match the XP login credentials.As an absolute statement of requirements that is not correct.

You could create a guest share and allow everyone on the LAN to access the share.

You could create a share that requires credentials but if this is being used in a peer-to-peer type of situation where the Linux user wants to share some files with Windows user then you might want to think twice about requiring the Windows user to give you his login username and password. He/She might not want you to have logon access to their physical machine. That's would be silly.

Now if you want to set up a server and you are the Systems Administrator and have control over all the machine in the network then yes it might be advantageous to have a linux user and samba password that matches the Windows client's username and password.

---

### Post by azmyth on 2011-09-29
You're correct on the XP is you just want to share a drive. If you want to share a printer, I couldn't figure out how to do it without matching the credentials.

---

### Post by Morbius1 on 2011-09-30
> **azmyth said:**
> You're correct on the XP is you just want to  share a drive. If you want to share a printer, I couldn't figure out how  to do it without matching the credentials.
Go into /etc/samba/smb.conf and look for the [printers] section. It should look like this:
> [printers]
    comment = All Printers
    browseable = No
    path = /var/spool/samba
    printable = yes
[COLOR=Blue]**     guest ok = no**[/COLOR]
    read only = yes
    create mask = 0700
Change it to this:
> [printers]
    comment = All Printers
    browseable = No
    path = /var/spool/samba
    printable = yes
[COLOR=Blue]**     guest ok = yes**[/COLOR]
    read only = yes
    create mask = 0700
Then restart samba:
```
sudo service smbd restart
```

---

### Post by Morbius1 on 2011-09-30
Mr.BadExample, if you're still out there please post the output of the following commands:
```
net usershare info --long
``````
testparm -s
```If you are using samba I think I may know the problem with the sharing of the ntfs partition and it's a simple fix but we need the info from the above commands to verify.

---

### Post by Mr.BadExample on 2011-09-30
> **Morbius1 said:**
> Mr.BadExample, if you're still out there please post the output of the following commands:
```
net usershare info --long
``````
testparm -s
```If you are using samba I think I may know the problem with the sharing of the ntfs partition and it's a simple fix but we need the info from the above commands to verify.


here is what I have coming up within the terminal
```

[backupstorage]
path=/media/Backup & Storage
comment=
usershare_acl=Everyone:F,
guest_ok=y

[sylvia's]
path=/media/Backup & Storage/Sylvia
comment=
usershare_acl=Everyone:F,
guest_ok=y

[public]
path=/home/james/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y

[josh's]
path=/media/Backup & Storage/Josh
comment=
usershare_acl=Everyone:F,
guest_ok=y

[storage]
path=/media/Backup & Storage
comment=Backup Drive on Ubuntu
usershare_acl=Everyone:F,
guest_ok=y

[sylvia]
path=/media/Backup & Storage/Sylvia
comment=
usershare_acl=Everyone:F,
guest_ok=y

```

```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Backup & Storage]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    security = SHARE
    encrypt passwords = No
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
    read only = No
    guest ok = Yes

[Backup & Storage]
    path = /media/Backup & Storage
    read only = No
    guest ok = Yes


```

---

### Post by Morbius1 on 2011-09-30
I'm going to guess that /media/Backup & Storage is the NTFS mountpoint and I'm betting that you are not mounting it through fstab but mounting it through Places or Nautilus. If all that's true the fastest way out of your dilemma is to edit /etc/samba/smb.conf and add the following line in the [global] section:
```
force user = james
```Then restart samba:
```
sudo service smbd restart
```As for the rest of the output it's a bit of a mess really. You have /media/Backup & Storage shared using 2 completely different methods 3 distinct times:

Usershares ( created from Nautilus ):
> [backupstorage]
path=/media/Backup & Storage
comment=
usershare_acl=Everyone:F,
guest_ok=y

[storage]
path=/media/Backup & Storage
comment=Backup Drive on Ubuntu
usershare_acl=Everyone:F,
guest_ok=yClassic Share ( in smb.conf ):

> [Backup & Storage]
    path = /media/Backup & Storage
    read only = No
    guest ok = Yes You can get rid of at least 2 of them. 

And the sylvia's, josh's, and sylvia shares are unnecessary since they all have access to the parent share of [backupstorage].

---

### Post by Mr.BadExample on 2011-10-02
Yeah I fairly new to Linux, Morbius. I spent a good chunk of time googling info to try and get is setup myself. All those extra entries would explain why I had so many extra network places showing in Win7 but errors about misspelled names and the like.

Will work it out after work today. Thanks for the info

---

