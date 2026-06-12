---
title: "Trouble setting up Ubuntu network"
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by user333 on 2011-04-23
Basically, I can communicate to Windows perfectly (Internet sharing,  file sharing, printer sharing, etc), but Windows controls everything,  and I can't access any other Ubuntu PC, or host a printer or Internet  connection.

I have been fighting Samba for quite a long time, and I finally am able to access Windows shares from Ubuntu, but I want to host the shared folders (and everything else) on Ubuntu instead, because I have a bigger HD on it, and it is just a faster computer. I tried personal file sharing and shared folders, but it doesn't work. I am also not able to access other Ubuntu PCs in the network, for printing, remote desktop, or file-sharing.

All the computer are connected to the same Ethernet router. I'm using XP Home SP3, Ubuntu 10.04 x64, and a laptop running 11.04 beta 2.

Does anyone know what I am doing wrong? All I want my desktop to "run" the network.

---

### Post by Morbius1 on 2011-04-23
From whatever Ubuntu machine that you want as the server post the output of the following commands:
```
testparm -s
net usershare info --long
smbtree
```

---

### Post by user333 on 2011-04-23
Here it is:

```
user333@user333-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[netlogon]"
NOTE: Service netlogon is flagged unavailable.
Processing section "[profiles]"
NOTE: Service profiles is flagged unavailable.
Processing section "[printers]"
Processing section "[pdf-documents]"
NOTE: Service pdf-documents is flagged unavailable.
Processing section "[pdf-printer]"
Processing section "[ubuntusharefolder]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
    workgroup = MSHOME
    netbios name = SAMBA24
    server string = Samba file and print server
    interfaces = 127.0.0.1/8, 192.168.0.0/24
    bind interfaces only = Yes
    encrypt passwords = No
    update encrypted = Yes
    client schannel = No
    server schannel = No
    allow trusted domains = No
    obey pam restrictions = Yes
    passwd program = /usr/bin/passwd '%u'
    passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
    passwd chat timeout = 120
    username map = /etc/samba/smbusers
    password level = 6
    username level = 6
    unix password sync = Yes
    log file = /var/log/samba/samba.log
    max log size = 1000
    name resolve order = wins lmhosts bcast
    client signing = No
    client use spnego = No
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = cups
    machine password timeout = 120
    add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
    delete user script = /usr/sbin/userdel '%u'
    add group script = /usr/sbin/groupadd '%g'
    delete group script = /usr/sbin/groupdel '%g'
    add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
    delete user from group script = /usr/sbin/userdel '%u' '%g'
    add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
    logon script = %G.bat
    logon path = \\%L\profiles\%u
    logon drive = m:
    logon home = \\%L\homes\%u
    os level = 33
    local master = No
    domain master = No
    dns proxy = No
    wins server = familynew
    remote announce = 192.168.0.255
    remote browse sync = 192.168.0.255
    idmap uid = 16777216-33554431
    idmap gid = 16777216-33554431
    template shell = /dev/null
    winbind separator = @
    winbind cache time = 360
    winbind use default domain = Yes
    winbind trusted domains only = Yes
    winbind nested groups = No
    winbind nss info = no
    hosts allow = 127., 192.168.0.
    cups options = raw
    follow symlinks = No

[homes]
    comment = Home Directories
    path = /home
    read only = No
    locking = No
    strict locking = No

[netlogon]
    comment = Network Logon Service
    path = /home/netlogon
    browseable = No
    browsable = No
    locking = No
    strict locking = No
    available = No

[profiles]
    comment = User Profiles
    path = /var/samba/profiles
    create mask = 0600
    directory mask = 0700
    browseable = No
    browsable = No
    locking = No
    strict locking = No
    available = No

[printers]
    comment = All Printers
    path = /var/spool/samba
    printable = Yes
    browseable = No
    browsable = No
    locking = No
    strict locking = No

[pdf-documents]
    comment = Converted PDF Documents
    path = /home/pdf-documents
    read only = No
    browseable = No
    browsable = No
    locking = No
    strict locking = No
    available = No

[pdf-printer]
    comment = PDF Printer Service
    path = /tmp
    guest ok = Yes
    printable = Yes
    printing = bsd
    print command = /usr/bin/gadmin-samba-pdf %s %u
    lpq command = 
    use client driver = Yes

[ubuntusharefolder]
    comment = a shared folder
    path = /home/user333/sharefolder
    read only = No
    guest ok = Yes
user333@user333-desktop:~$ net usershare info --long
info_fn: file /var/lib/samba/usershares/sharedfolder is not a well formed usershare file.
info_fn: Error was Path is not a directory.
user333@user333-desktop:~$ smbtree
Enter user333's password: 
user333@user333-desktop:~$
```

---

### Post by Morbius1 on 2011-04-23
First, Dont use gadmin-samba anymore or else you will end up having an smb.conf like that and you won't have any friends.

You do have one immediate problem and that's one line:
>      encrypt passwords = No
Change it to yes and restart samba
```
sudo service smbd restart.
```
As for the rest of that smb.conf I'm not touching it - life's too short.

If you would like to start over again with a factory fresh smb.conf let me know.

---

### Post by user333 on 2011-04-23
How would I get a new smb.conf?

---

### Post by Morbius1 on 2011-04-23
There's one at  /usr/share/samba/smb.conf:

Here's a step by step if your interested: [http://ubuntuforums.org/showpost.php?p=9505697&postcount=13](http://ubuntuforums.org/showpost.php?p=9505697&postcount=13)

---

### Post by user333 on 2011-04-23
Ok! Thanks for the link :) I'll look at that.

---

### Post by user333 on 2011-04-23
Thanks :) Doing what that link said made everything work perfectly :)

---

