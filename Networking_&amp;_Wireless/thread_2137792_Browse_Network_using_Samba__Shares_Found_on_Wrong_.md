---
title: "Browse Network using Samba :: Shares Found on Wrong Workgroup Ubuntu 11.10"
date: 2013-04-22
forum: Networking &amp; Wireless
---

### Post by own3mall on 2013-04-22
I've read several threads regarding the setup and use of Samba, and Samba has always been working fine until recently.  I didn't change anything, but for some reason, it appears that Samba only resolves hosts on the default "Workgroup" workgroup.  However, the /etc/samba/smb.conf file is setup to use a different workgroup.  None of the hosts resolve on this workgroup, but all of my Windows machines can see each other.  Any idea what's wrong?

Here's the output of my settings:

```

testparm /etc/samba/smb.conf
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    workgroup = ERICSNET
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
    name resolve order = wins bcast lmhosts host
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


```  

All I want to be able to do is access my NAS drive over the network via Samba.  

Do any of my config settings look wrong?  It's as if Samba is ignoring the workgroup setting and still going with "Workgroup".  Any help is appreciated!

---

