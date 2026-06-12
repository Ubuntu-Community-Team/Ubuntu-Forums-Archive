---
title: "Samba Linux to Linux share"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by CyberRascal on 2010-01-30
Hi. I'm trying to share a disk partition from my karmic koala setup to my other karmic setup.

This is the output from testparm smb.conf:

[PHP]
[global]
        netbios name = MAX-SAMBA-SRV
        server string = max-server (Samba, Ubuntu)
        interfaces = eth1
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

[sdb2]
        comment = Data disk
        path = /dev/sdb2
        read only = No
        guest ok = Yes

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
[/PHP]

However, smbtree yields the following result:

[PHP]
WORKGROUP
        \\UBUNTU                        ubuntu server (Samba, Ubuntu)
                \\UBUNTU\sdb2                   Data disk
                \\UBUNTU\print$                 Printer Drivers
                \\UBUNTU\IPC$                   IPC Service (max-server (Samba, Ubuntu))
[/PHP]

Why does the server string show up after IPC Service? Why is the netbios name UBUNTU and not MAX-SAMBA-SRV? I mean, I set it up to share /dev/sdb2 which it evidently does, so UBUNTU must be my samba server.

Running smbtree on my second machine yields the following result:

[PHP]

WORKGROUP
      \\UBUNTU            ubuntu server (Samba, Ubuntu)
cli_start_connection: failed to connect to UBUNTU<20> (0.0.0.0) NT_STATUS_CONNECTION_REFUSED

[/PHP]

Any idea what I can do next?

---

### Post by Morbius1 on 2010-01-30
A lot of excellent questions. Not sure if I'm the one to answer them all but I would like to focus on one aspect first:
> [COLOR=#000000][COLOR=#007700][[/COLOR][COLOR=#0000BB]sdb2[/COLOR][COLOR=#007700]]
        [/COLOR][COLOR=#0000BB]comment [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]Data disk
        path [/COLOR][COLOR=#007700]= /[/COLOR][COLOR=#0000BB]dev[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]sdb2
        read only [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]No
        guest ok [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]Yes[/COLOR][/COLOR]

I'm fairly certain you can't share a device. You can share a mount point to that device but not the device itself. You need to mount the device preferably in fstab so that it always mounts on boot.

---

### Post by Morbius1 on 2010-01-30
You've also got something missing from your [global] section. ( Actually you've got a lot of things missing from the standard default global section ).
```
 map to guest = Bad User
```You've declared the share to allow guest access but you haven't given smb.conf the tool to determine what a guest is. 

A "Bad User" is a remote user that either has not authenticated himself correctly if attempting to access a private share or a guest who isn't required to authenticate himself for access to a public share so has no password. Without the "map to guest" line samba has no way to convert those remote users to "guest". From the samba manpages for "map to guest":
> Note that this parameter is needed to set up "Guest"      share services when using *security* modes other than      share and server.. And your security mode is "user" as it should be - it's the default.

FYI, some of the other things that are missing from the default Ubuntu smb.conf are these:
```

    obey pam restrictions = Yes
    passdb backend = tdbsam
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    
```Now all of these are related to samba users and passwords which don't affect you since you only have the one public share so you don't need any samba users or passwords. You certainly don't need to create any samba passwords anyway. I'm just not sure if they need to be present anyway.

Was this smb.conf built from some kind of utility or did you roll your own?

---

