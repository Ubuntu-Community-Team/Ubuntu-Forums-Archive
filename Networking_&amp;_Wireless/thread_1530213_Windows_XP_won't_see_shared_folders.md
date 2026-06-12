---
title: "Windows XP won't see shared folders"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by malcmail on 2010-07-13
Now I've got the printers working its time to file share.
 
Lucid Lynx and Windows XP - both machines ping each other. When I go to entire netweork on XP and click on server all it gives me is Printers and Faxes - none of the folders I've shared. In the smb.conf file I have force user = xxx that I ahd seen elsewhere.  What am I missing?

---

### Post by Morbius1 on 2010-07-13
What method of samba did you use - there are two. Post the output of these commands so we can see what method you are using and how you are using it:
```
net usershare info
sudo net usershare info
testparm -s
```

---

### Post by malcmail on 2010-07-13
Ready armed having seen that question ;) - the first 2 return nothing (although I'm in sudo su anyway).  Testparm gives:-

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[cdrom]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = HOUSE
    server string = %h server (Samba, Ubuntu)
    security = SHARE
    map to guest = Bad User
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    printcap name = cups
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    comment = Home Directories
    force user = me
    browseable = No
    browsable = No

[printers]
    comment = All Printers
    path = /var/spool/samba
    read only = No
    create mask = 0700
    guest only = Yes
    guest ok = Yes
    printable = Yes
    use client driver = Yes

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    browseable = Yes
    browsable = Yes

[cdrom]
    comment = Samba server's CD-ROM
    path = /cdrom
    guest ok = Yes
    locking = No


PS Do you ever take a break? ;)

---

### Post by Morbius1 on 2010-07-13
You've got a couple of odd things going on there:

>      security = SHAREThe preferred security is user not share.
> browseable = No
    browsable = NoThe option browsable = no will render your shares invisable to the network. Either delete those lines or comment them out.

But the biggest problem you have is you have no shares defined so even if you remove the "browseable = no" line there is nothing for the remote user to see.

What type of shares would you like to create? Accessible by guests without the use of a samba password or  are your requirements more complicated than that?

---

### Post by malcmail on 2010-07-13
I'll check the smb file for those changes. What I would like it to do is for any of a number of PCs with different users to access photos, music etc on the server without the need to log in to the server. Nothing more complex than that.  WHy would there be no shares shown as I've used the file manager type package to share a number of folders? Or is this something different?

---

### Post by malcmail on 2010-07-13
Very confused - the results of testparm had printers not browseable but the smb.conf I have in /etc/samba shows the following :

[printers]
   comment = All Printers
   browseable = yes
public = yes
   path = /var/spool/samba
#path = /tmp
   printable = yes
   guest only = yes
   read only = no
   create mode = 0700
use client driver = yes

---

### Post by malcmail on 2010-07-13
And suddenly it works!  

Thanks again for your help fella. Maybe I can give you peace for a little while now ;)

---

