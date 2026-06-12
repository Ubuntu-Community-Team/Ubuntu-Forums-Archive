---
title: "smbtree returns nothing"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by almogaver on 2009-04-02
I am using a Windows Vista desktop with VmWare.
On a virtual machine (bridged network) I have installed Ubuntu Server 8.10 and Samba 3.2.3.
I can mount remote shares on Windows Vista machines (as long as I write "ip=xxx.xxx.xxx.xxx" in the options and I can list the shares with "smbclient -L <NETBIOS NAME> -U <user%password>".

But smbtree refuses to display any results. I have tried it with several combinations and it comes back empty. I have even run it with "-d 10" and I can see that it is interacting with the host (at least I can see its name and OS details in the messages).

By the way, there is no Domain Server on the network and all computers have the same workgroup: WORKGROUP.

I would appreciate if someone shed some light on this matter.


This is smb.conf (as dumped by testparm):
```
[global]
        netbios name = UBUNTUSVR2
        server string = %h server (Samba, Ubuntu, 3)
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        name resolve order = lmhosts host wins bcast
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

---

### Post by almogaver on 2009-04-02
All right, I have rebooted the host and now it seems to be working. Before this I had restarted the Guest several times to no avail.

I love magic!
:-k

---

