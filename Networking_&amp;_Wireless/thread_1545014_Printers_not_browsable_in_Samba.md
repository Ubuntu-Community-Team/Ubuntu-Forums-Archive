---
title: "Printers not browsable in Samba"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by TurboZinc on 2010-08-03
I've setup a print server using lucid and i'm a bit confused with the samba configuration. I have the printers listed as browsable in /etc/samba/smb.conf, but testparm says the are not. I've found that the printers show up in the share every now and then. Not sure what's going on.

```
testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Documents]"
Processing section "[XPhome]"
Loaded services file OK.
'winbind separator = +' might cause problems with group membership.
Server role: ROLE_DOMAIN_MEMBER
Press enter to see a dump of your service definitions

[global]
    workgroup = AWORKGROUP
    realm = ACOMPANY.CORP
    server string = %h server (Ubuntu Lucid)
    security = ADS
    obey pam restrictions = Yes
    log level = 3
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    printcap name = cups
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap uid = 6000-20000
    idmap gid = 6000-20000
    template shell = /bin/bash
    winbind separator = +
    winbind enum users = Yes
    winbind enum groups = Yes
    winbind use default domain = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    use client driver = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

```and here is my samba configuration file. Notice browsable is set to yes. Is this configurable somewhere else?
```
[global]
   workgroup = AWORKGROUP
   realm = ACOMPANY.CORP
   preferred master = no
   security = ADS
   encrypt passwords = yes
   log level = 3
   log file = /var/log/samba/log.%m
   max log size = 100
   printcap name = cups
   printing = cups
   winbind enum users = Yes
   winbind enum groups = Yes
   winbind use default domain = Yes
   winbind nested groups = yes
   winbind separator = +
   idmap uid = 6000-20000
   idmap gid = 6000-20000
   template shell = /bin/bash
   server string = %h server (Ubuntu Lucid)
   dns proxy = no
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   obey pam restrictions = yes

[printers]
   comment = All Printers
   path = /var/spool/samba
   browseable = Yes
   browsable = Yes
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
   use client driver = yes

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = Yes
   read only = Yes
   guest ok = No
```

---

### Post by Morbius1 on 2010-08-04
You've go a couple of things going on.

First, You've got "browseable = Yes" yet testparm says no you don't. That will always happen becasue you have "printable = yes". The "browseable" doesn't refer to the printers available on the server, it refers to the [COLOR=Blue][printers][/COLOR] share itself. And you have to have "printable = yes" or else you won't be able to spool the print job to **path = /var/spool/samba**

Second, Here's my guess on what's going on: Because of the way upstart services are started in 10.04, cups may be starting after samba is started. Samba on startup creates a printer share dynamically for every printername it finds in the CUPS configuration files. No CUPS - No printer list.

To test my theory reboot the machine and execute the following command:
```
smbtree
```If it does not list your printers then restart samba:
```
sudo service smbd restart
```Then do an "smbtree" again. Do you see your printer list?

[COLOR=Blue]EDIT: Just noticed that you're using 9.10. I think the correct way to restart samba in 9.10 is:[/COLOR]
```
      sudo service samba restart 
```
Although based on how you set up your smb.conf I'm guessing you already knew that :wink:

---

### Post by Morbius1 on 2010-08-04
Repeated post for some reason

---

### Post by TurboZinc on 2010-08-04
You're correct that restarting samba after the computer boots does list the printers in smbtree.

I should have mentioned it earlier, but this is a headless 10.04 server install.

---

### Post by Morbius1 on 2010-08-04
I must be getting old and feeble minded :p

See if this permanently fixes your problem: [http://ubuntuforums.org/showthread.php?p=9605764#post9605764](http://ubuntuforums.org/showthread.php?p=9605764#post9605764)

---

### Post by TurboZinc on 2010-08-04
> **Morbius1 said:**
> I must be getting old and feeble minded :p

See if this permanently fixes your problem: [http://ubuntuforums.org/showthread.php?p=9605764#post9605764](http://ubuntuforums.org/showthread.php?p=9605764#post9605764)

Problem looks to be fixed now. Thanks for the help.

---

