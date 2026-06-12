---
title: "Sharing files between two ubuntu machines?"
date: 2006-01-06
forum: Networking &amp; Wireless
---

### Post by diggs on 2006-01-06
So both machines are running ubuntu, breezy browser. Connected through a router. I have installed automatix if that helps. I have tried this:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)
and this:
[http://ubuntuguide.org/#automountnetworkfoldersall](http://ubuntuguide.org/#automountnetworkfoldersall)
and this
[http://ubuntuguide.org/#sharefolderstheeasyway](http://ubuntuguide.org/#sharefolderstheeasyway)
as well as this NFS business, which I couldn't figure out because I'm a n00b and/or a complete moron. 

So, moving forward:
I have some partitions on my harddrive of the desktop, hda1,5,6,7,8,9 that I want to share with my laptop. remember, both are running on ubuntu.

my desktop is 192.168.1.100
my laptop is 192.168.1.102

On my desktop, when I right click on a folder within the partition and select "share folder" nothing happens. I have samba installed on both machines.

I would like to be able to read and write to the files as well. For the time being I will be happy with having a wired connection, then sorting out a wireless one.

It should be noted that this is hella frustrating and really getting on my nerves, so a simple, step by step explenation would be just lovely. Thanks!

---

### Post by diggs on 2006-01-06
allright, so I did this:
[http://ubuntuguide.org/#sharepublicfoldersreadwritesecurityuser](http://ubuntuguide.org/#sharepublicfoldersreadwritesecurityuser)

```

derek@ubuntu:~$ sudo mkdir /home/group
derek@ubuntu:~$ sudo chmod 777 /home/group/
derek@ubuntu:~$ sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
derek@ubuntu:~$ sudo gedit /etc/samba/smb.conf
derek@ubuntu:~$ sudo testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Group]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

# Global parameters
[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam, guest
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
        username map = /etc/samba/smbusers
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[homes]
        comment = Home Directories
        read only = No
        create mask = 0700
        directory mask = 0700
        browseable = No

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[Group]
        comment = Group Folder
        path = /home/group
        valid users = system_username1, system_username2
        force user = nobody
        force group = nogroup
        read only = No
        create mask = 0700
        directory mask = 0700
        guest ok = Yes
derek@ubuntu:~$ sudo gedit /etc/samba/smb.conf
derek@ubuntu:~$ sudo testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Group]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

# Global parameters
[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam, guest
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
        username map = /etc/samba/smbusers
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[homes]
        comment = Home Directories
        read only = No
        create mask = 0700
        directory mask = 0700
        browseable = No

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[Group]
        comment = Group Folder
        path = /home/group
        valid users = derek
        force user = nobody
        force group = nogroup
        read only = No
        create mask = 0700
        directory mask = 0700
        guest ok = Yes
derek@ubuntu:~$ sudo /etc/init.d/samba restart
 * Stopping Samba daemons...                                             [ ok ]
 * Starting Samba daemons..                                              [ ok ]
derek@ubuntu:~$

```
now WTF do I do? I still haven't figured anything out! I have really no clue what to do, how to share anything. what am I doing wrong? all I want to do is share the bloody hda9 partition on my desktop with my laptop...

---

### Post by lixy on 2006-01-13
Try this out:[http://www.pcworld.idg.com.au/index.php/id;1795587325;fp;512;fpid;1783981662]("http://www.pcworld.idg.com.au/index.php/id;1795587325;fp;512;fpid;1783981662")
Tweak it to suit ubuntu by replacing nfs by nfs-common. Don't forget to sudo!

---

