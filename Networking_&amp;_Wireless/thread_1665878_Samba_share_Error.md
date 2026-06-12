---
title: "Samba share Error"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by wes.k.edens on 2011-01-12
I am getting this error when I try to share a folder through samba. 

**Error 255 cannot convert name "Everyone" to a SID**

I have searched the forums and tried all the fixes, but I still cannot seem to get it to work. I will try to post all the info that everyone usually asks for. 

---------------------------------------------------------------------------------------------------------------
wedens@wedens-Desktop:~$ service smbd status
smbd start/running, process 7672

---------------------------------------------------------------------------------------------------------------

//Permissions for the folder i want to share
wedens@wedens-Desktop:/home$ ls -l
total 8
drwxrwxrwx  2 wedens users  4096 2010-09-26 17:14 samba

---------------------------------------------------------------------------------------------------------------

wedens@wedens-Desktop:/home$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[samba]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    workgroup = NETWORK-WEDENS
    server string = %h server (Samba, Ubuntu)
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
    usershare owner only = No
    panic action = /usr/share/samba/panic-action %d

[homes]
    comment = Home Directories
    read only = No
    create mask = 0775
    directory mask = 0775

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

[samba]
    path = /home/samba
    read only = No
    guest ok = Yes
---------------------------------------------------------------------------------------------------------------

I do not have a file /etc/init.d/samba  Has this been replaced by /etc/init.d/smbd ?

Also, I have a /var/lib/samba/usershares folder but it is empty. Is there supposed to be something inside?

I would really appreciate any help. 

Thank You

---

### Post by wes.k.edens on 2011-01-14
I have tried changing another property:

win_support = true

but this still did not help. I tried uninstalling samba and starting again, but I am still  getting the same error. 

Can someone please help

---

### Post by dandnsmith on 2011-01-15
Is that really the exact error shown?
In what context does it occur? (what did you do just before it is shown?)
I'm a bit concerned about your network group name - if you try that with some Windows versions, you'll find it won't work because it is:
1) too long
2) has a non-permitted character in the middle (Hyphon)

It is also a mistake to put spaces in the names.

---

### Post by Morbius1 on 2011-01-15
You're mixing two completly different methods of sharing folders in Samba.

One of them is called Usershares and Gnome has  implemented it using a package called nautilus-share that allows a user to share folders directly from Nautilus itself. The " **Error 255 cannot convert name "Everyone" to a SID " **error is a Nautilus-share error. Usershares keeps it's share definitions at /var/lib/samba/usershares so it's not a surprise that it's empty.

The other method is called Classic-shares and it keeps it's share definitions within smb.conf itself. You already have a share definition for /home/samba in smb.conf so my advice is simple: don't use nautilus-share.

The reason you are having a problem accessing your "samba" share is because you have a parameter set wrong:

This:
>      encrypt passwords = NoShould be this:
>      encrypt passwords = YesThen restart samba:
```
sudo service smbd restart
```BTW:
>  I do not have a file /etc/init.d/samba  Has this been replaced by /etc/init.d/smbd ?Actually, it's been replaced by /etc/init/smbd.conf. /init.d/smbd is actually a link that goes someplace else. The samba daemon is now under the control of Upstart so things are a little complicated. Just use the "sudo service smbd .. " command and you'll be fine.

---

### Post by wes.k.edens on 2011-01-15
Thank You so much Morbius1

Changing the encrypt passwords property to yes fixed everything. I can now access everything from the network.

---

### Post by brett- on 2012-04-30
Changing encrypted from "no" to "yes" in U-12.04 worked for me also, thanks.):P

---

