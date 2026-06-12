---
title: "Two ubunu systems only one available in &quot;Network&quot;"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by astembridge on 2010-01-18
Hi, I have two ubuntu systems on my local network.  Both have internet connectivity and can ping each other.  I can SSH in to both machines (going both ways). 

I set up a public share folder on both systems.   On system A, the system and public folder appear under "Network".   On system B, the system does not appear in "Network".  

I've shared the public folder on System B by right-clicking and going to Share, then opening it up for read/write and guest access (local secure network, for testing).    I've also installed Samba server and added a share with full read/write, guest access.    I've rebooted..  Nothing I do makes this system appear on the network.   

Again, I can ping System B, and ssh into the machine no problems.   

Help?

---

### Post by astembridge on 2010-01-19
Can anyone take a crack at this?

---

### Post by Morbius1 on 2010-01-19
Just to get some preliminary data, please post the output of the following commands:

On System B:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**
Type **smbtree**

The first thing I would do is to disable any firewalls you may have configured yourself and see if you can share folders.

[COLOR=Blue]EDIT: There is one more thing. It seems to be a problem with Karmic. When you first boot see if samba is running:[/COLOR]

Open **Terminal**
Type [B]sudo service samba status
[/B]
If it's not, start it with: **sudo service samba restart**

---

### Post by astembridge on 2010-01-19
Ok I'll post back when I get home tonight.

---

### Post by Xog on 2010-01-19
posting for view later, having similar problem

---

### Post by astembridge on 2010-01-19
> **Morbius1 said:**
> [COLOR=Blue]EDIT: There is one more thing. It seems to be a problem with Karmic. When you first boot see if samba is running:[/COLOR]

Open **Terminal**
Type [B]sudo service samba status
[/B]
If it's not, start it with: **sudo service samba restart**

Just a quick note to your edit..    Samba server is running (I restarted the service several times).

---

### Post by astembridge on 2010-01-19
Type [B]net usershare info

[/B]
```
astembridge@sol:~$ net usershare info
[desktop]
path=/home/astembridge/Desktop
comment=
usershare_acl=Everyone:F,
guest_ok=n

[bu_emerald]
path=/music/backup_emerald
comment=
usershare_acl=Everyone:F,
guest_ok=n
```[INDENT]
**astembridge@sol:~$ **

[/INDENT]Type **testparm -s**

```
[global]
    netbios name = SAMBA24
    server string = sol
    interfaces = 127.0.0.1/8, 192.168.0.0/24
    update encrypted = Yes
    client schannel = No
    server schannel = No
    allow trusted domains = No
    obey pam restrictions = Yes
    passwd program = /usr/bin/passwd '%u'
    passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
    passwd chat timeout = 120
    username map = /etc/samba/smbusers
    password level = 8
    username level = 8
    unix password sync = Yes
    log file = /var/log/samba/samba.log
    max log size = 1000
    name resolve order = wins lmhosts bcast
    client signing = No
    client use spnego = No
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = /etc/printcap
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
    share modes = No

[netlogon]
    comment = Network Logon Service
    path = /home/netlogon
    read only = No
    locking = No
    share modes = No

[profiles]
    comment = User Profiles
    path = /var/samba/profiles
    read only = No
    create mask = 0600
    directory mask = 0700
    browseable = No
    locking = No

[printers]
    comment = All Printers
    path = /var/spool/samba
    printable = Yes
    browseable = No
    locking = No
    share modes = No

[pdf-documents]
    comment = Converted PDF Documents
    path = /home/pdf-documents
    read only = No
    guest ok = Yes

[pdf-printer]
    comment = PDF Printer Service
    path = /tmp
    guest ok = Yes
    printable = Yes
    printing = bsd
    print command = /usr/bin/gsambadpdf %s %u
    lpq command = 
    use client driver = Yes

[music]
    path = /music
    read only = No
    guest ok = Yes

[Desktop]
    path = /home/astembridge/Desktop
    valid users = astembridge, root, smbguest
    read only = No

[musiccollection]
    path = /musiccollection
    read only = No
    guest ok = Yes

[backup_emerald]
    path = /music/backup_emerald
    read only = No
    guest ok = Yes
```Type **smbtree**

- this asks for a password.  After entering the pw, it returns to a prompt with no information.

---

### Post by Morbius1 on 2010-01-20
Oh, dear lord, are you studying to pass a red hat systems administrator certification exam? ;)

I'm afraid most of that is beyond me but I would suggest the following:

Nautilus-share:
> [desktop]
path=/home/astembridge/Desktop
comment=
usershare_acl=Everyone:F,
[COLOR=Blue]guest_ok=n
[/COLOR] 
[bu_emerald]
path=/music/backup_emerald
comment=
usershare_acl=Everyone:F,
[COLOR=Red]guest_ok=n[/COLOR]Classic Samba:
> [Desktop]
    path = /home/astembridge/Desktop
    [COLOR=Blue]valid users = astembridge, root, smbguest[/COLOR]
    read only = No

[backup_emerald]
    path = /music/backup_emerald
    read only = No
    [COLOR=Red]guest ok = Yes[/COLOR]
You're using two completly different sharing methods ( with different configuration files: /var/lib/samba/usershares vs smb.conf ) on the same target directory with different privileges. I would suggest deleting the nautilus-share shares:

Open **Terminal**
Type **net userhsare delete desktop**
Type [B]net usershare delete bu_emerald

[/B]This will eliminate the sharing of, not the actual target directory.You can also just go into Nautilus and right click those targets and simply "unshare" them.

Also, I would suggest you think about the sharing of your desktop. Things can be executed on the desktop and represents a greater risk that just a regular shared directory. But that's up to you.

As for the rest of your smb.conf and what impact that has on remote access, I'm going to need some time to understand and think through all that. The fact that you can see the remote share is good, the fact that you're denied access I think is in your smb.con file somewhere just not sure where.

The only other thing I can think of is the problem of linux permissions.
For example you're allowing guest access to /music/backup_emerald.
Samba may allow guest access but it can't override linux file permissions. You have to allow "others" read / write access on the directory itself for the remote guest to have access.

If you do a **ls -dl /music/backup_emerald** the permissions should look like this:> drwxrwxrwx

---

### Post by astembridge on 2010-01-20
(double post)

---

### Post by astembridge on 2010-01-20
[LIST]
[*]All netshares have been deleted
[*]The bu_emerald folder has drwxrwxrwx
[*]Samba server has been restarted (service samba restart)
[/LIST]

Still no shares visible from System A (or any other computer on my local network).   As before, I can ping and ssh into System B.

---

### Post by Morbius1 on 2010-01-20
I'm fairly certain that I can't help you I'm afraid. The more I look at that smb.conf the more I realize that I'm not qualified to comment. If this was a typical linux machine offering shares to the home network, I might be of some assistance. But from the looks of it I think your question belongs in the Server part of this forum:

[http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339)

The folks over there rarely come over here.

---

