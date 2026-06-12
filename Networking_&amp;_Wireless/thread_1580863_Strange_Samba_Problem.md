---
title: "Strange Samba Problem"
date: 2010-09-24
forum: Networking &amp; Wireless
---

### Post by souta95 on 2010-09-24
I have been having off and on issues with my samba file shares.

I am sharing a NTFS formated hard drive where the mount point is in my home directory, as well as a printer connected via USB.

I am to the point where printing works (using it as an ipp print share, samba is configured for it, but I don't know if it works or not), and I can access the shared folder from Windows, but I can't access the shared folder from any Ubuntu machine.  I get the error:

```
**Could not display "smb:///<serveripaddress>".**

Error: Failed to retrieve share list from server
Please select another viewer and try again.
```

Using the server's host name yields the same results.  Windows XO Home Edition had trouble accessing via host name (couldn't even ping it), but I could access it via IP address.  Windows 7 Ultimate can access it via host name.  The server can be pinged from Ubuntu.  The server has a static IP address.  All Linux machines are Ubuntu 10.04 with the latest updates.

There have been times I was able to access the server from my laptop running Ubuntu, but I don't know what I did to get it to work, and I didn't change anything and it quit working.

my smb.conf:

```
[global]
;    netbios name = <servername>

    workgroup = workgroup
    usershare allow guests = yes
    security = share
    guest ok = yes
    hosts allow = 127.0.0.1/8 192.168.1.0/24
    interfaces = 127.0.0.1/8 192.168.1.0/24
    bind interfaces only = yes
    remote announce = 192.168.1.255
    remote browse sync = 192.168.1.255
    printcap name = cups
;    load printers = yes
    cups options = raw
;    printing = cups
    guest account = smbguest
    log file = /var/log/samba/samba.log
    max log size = 1000
;    null passwords = no
    username level = 6
    password level = 6
;    encrypt passwords = yes
    unix password sync = yes
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    local master = no
    domain master = no
;    preferred master = no
;    domain logons = no
    os level = 33
    logon drive = m:
    logon home = \\%L\homes\%u
    logon path = \\%L\profiles\%u
    logon script = %G.bat
;    time server = no
    name resolve order = wins lmhosts bcast
;    wins support = no
;    wins proxy = no
    dns proxy = no
;    preserve case = yes
;    short preserve case = yes
    client use spnego = no
    client signing = no
    client schannel = no
;    server signing = no
    server schannel = no
;    nt pipe support = yes
;    nt status support = yes
    allow trusted domains = no
    obey pam restrictions = yes
    enable spoolss = yes
;    client plaintext auth = no
;    disable netbios = no
    follow symlinks = no
    update encrypted = yes
;    pam password change = no
    passwd chat timeout = 120
;    hostname lookups = no
;    smb passwd file = /etc/samba/smbpasswd
    passwd program = /usr/bin/passwd '%u'
    passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
    add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
    add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
    add group script = /usr/sbin/groupadd '%g'
    delete user script = /usr/sbin/userdel '%u'
    delete user from group script = /usr/sbin/userdel '%u' '%g'
    delete group script = /usr/sbin/groupdel '%g'
    add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
    machine password timeout = 120
    idmap uid = 16777216-33554431
    idmap gid = 16777216-33554431
    template shell = /dev/null
    winbind use default domain = yes
    winbind separator = @
    winbind cache time = 360
    winbind trusted domains only = yes
    winbind nested groups = no
    winbind nss info = no
;    winbind refresh tickets = no
;    winbind offline logon = no
;    server string = samba 3.4.7

[netlogon]
    comment = Network Logon Service
    path = /home/netlogon
    read only = no
;    available = yes

;    guest ok = no
;    printable = no
    locking = no
    strict locking = no

;    browsable = yes
[profiles]
    comment = User Profiles
    path = /var/samba/profiles
    read only = no
;    available = yes

;    guest ok = no
;    printable = no
    create mode = 0600
    directory mask = 0700
    locking = no
    strict locking = no

    browsable = no
[printers]
    comment = All Printers
    path = /var/spool/samba
;    browseable = yes
;    writable = no
    guest ok = yes
    printable = yes
    locking = no
    strict locking = no

[pdf-documents]
    path = /home/pdf-documents
    comment = Converted PDF Documents
;    available = yes


    guest ok = yes
    locking = no
    strict locking = no

;    browsable = yes
    writable = yes
[pdf-printer]
    path = /tmp
    comment = PDF Printer Service
    printable = yes
    guest ok = yes
    use client driver = yes
    printing = bsd
    print command = /usr/bin/gadmin-samba-pdf %s %u
    lpq command = 
    lprm command = 

[WDGREEN]
    path = /home/hidiki/WDGREEN
    writeable = yes
;    browseable = yes
    guest ok = yes
```

I have tried too many methods of configuration to count, so the file is pretty sloppy.

---

### Post by luvshines on 2010-09-24
What command are you using to access the share from Ubuntu ??

Your smb.conf also contains lots of winbind parameters, you using a DC for authentication ?

---

### Post by souta95 on 2010-09-24
I am trying to browse the shares from Nautilus.

I don't know what you mean by winbind or DC.

Its just a home network.  I don't want any passwords on the shares.

---

### Post by luvshines on 2010-09-25
I haven't tried setting up printer sharing, but for home/office network I do have Samba share working [ though it's password protected, office policies :P]

See if this helps (for password less shares)
[http://ubuntuforums.org/showthread.php?t=658056](http://ubuntuforums.org/showthread.php?t=658056)

I saw that you had lots of 'winbind' stuff and 'uid/gid' stuff in your smb.conf

Those kind of stuff is required when you are working with Active Directory [or other Domain Controllers (DC) ] hence asked :)

---

### Post by souta95 on 2010-09-25
It appears to be working now, thank you.

I had to add these to the [WDGREEN] section of smb.conf

```
	availible = yes
	public = yes
```

I also removed the ";" from the browseable line.

---

### Post by abir16 on 2010-09-28
Good decision. Once with the same problem encountered.

---

