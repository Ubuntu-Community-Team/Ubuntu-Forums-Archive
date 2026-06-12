---
title: "Desktop and laptop cannot see each other after upgrade"
date: 2013-01-02
forum: Networking &amp; Wireless
---

### Post by mtguy on 2013-01-02
Recently upgraded my desktop to 12.10 (32 bit) and now my laptop which runs 12.04 (64 bit) and desktop cannot see each other.  It's been a week or so since upgrading and I honestly don't remember how I responded when asked if I wanted to keep old samba config files, though I'm pretty sure I said to keep the old ones.  In any event, I did a search and ran the common commands requested for such problems and here are the results:
```
[jef@xubuntu-box] ~  Wed Jan 02
08:02 AM
~:testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "password level" option is deprecated
Unknown parameter encountered: "update encrypted"
Ignoring unknown parameter "update encrypted"
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
Processing section "[homes]"
Processing section "[netlogon]"
Processing section "[profiles]"
Processing section "[printers]"
Processing section "[pdf-documents]"
Processing section "[pdf-printer]"
Processing section "[home]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
    server string = Samba file and print server
    interfaces = 127.0.0.1/8, 192.168.0.0/24
    bind interfaces only = Yes
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
    remote announce = 192.168.0.255
    remote browse sync = 192.168.0.255
    template shell = /dev/null
    winbind separator = @
    winbind cache time = 360
    winbind use default domain = Yes
    winbind trusted domains only = Yes
    winbind nested groups = No
    winbind nss info = no
    idmap config * : range = 16777216-33554431
    idmap config * : backend = tdb
    hosts allow = 127., 192.168.0.
    cups options = raw
    follow symlinks = No

[homes]
    comment = Home Directories
    path = /home
    valid users = %U
    read only = No
    locking = No
    strict locking = No

[netlogon]
    comment = Network Logon Service
    path = /var/lib/samba/netlogon
    read only = No
    locking = No
    strict locking = No

[profiles]
    comment = User Profiles
    path = /var/lib/samba/profiles
    read only = No
    create mask = 0600
    directory mask = 0700
    locking = No
    strict locking = No

[printers]
    comment = All Printers
    path = /var/spool/samba
    printable = Yes
    print ok = Yes
    browseable = No
    locking = No
    strict locking = No

[pdf-documents]
    comment = Converted PDF Documents
    path = /var/lib/samba/pdf-documents
    admin users = %U
    read only = No
    guest ok = Yes
    locking = No
    strict locking = No

[pdf-printer]
    comment = PDF Printer Service
    path = /tmp
    guest ok = Yes
    printable = Yes
    print ok = Yes
    printing = bsd
    print command = /usr/bin/gadmin-samba-pdf %s %u
    lpq command = 
    use client driver = Yes

[home]
    path = /home
    read only = No
    guest ok = Yes

```and:
```
[jef@xubuntu-box] ~  Wed Jan 02
08:03 AM
~:smbtree
Ignoring unknown parameter "update encrypted"
Enter jef's password: 

```I confess that I know nothing about samba...though somehow I got it working when both machines had 12.04 and had no problems sharing files between them.  Thanks for any help!

---

### Post by TheFu on 2013-01-02
Sharing files between 2 Linux machines should not use samba. You probably want to use NFS or even sshfs instead. NFS supports almost the entire file permissions that UNIX OSes expect.

Only use samba if you have Windows PCs. Samba permission modes are terribly lacking.
It is also slower than NFS.

[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto) explains all.  Only use NFS on the same subnet, never over the internet (just like samba).  If you need over the internet file access, use sshfs. It is much slower, but works well enough with the appropriate expectations.
-----------------------------------------------------------------------
**Update for Samba below:**
However, if you still want Samba and like your current "shares", then I would

[LIST=1]
[*]save the current smb.conf file
[*]reinstall samba using **apt-get --reinstall install samba**
[*]accept the new files - let it overwrite
[*]compare the new files to my old, saved file
[*]merge the important differences
[*]restart samba on the server
[/LIST]
then test connections.


If that failed to work, I'd use the "samba howto guide" ... easily found with google [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba) and start over from scratch.

---

### Post by mtguy on 2013-01-03
Thanks for the info, TheFu.  I neglected to mention that the laptop came with Windows 7 and while I only log on once a month or so to update all the crap, I would still like to be able to communicate with the desktop, so I prefer to use samba.

Speaking of which, I purged both machines of samba and config files and reinstalled on each and they still cannot see each other.  It's not crucial, though it is a tad inconvenient and puzzling.

---

### Post by mtguy on 2013-01-03
Well, curiously, after rebooting the server, all is back as it should be...even though I had restarted the samba service, my laptop couldn't see the desktop...so I figured, why not?  I rebooted the desktop and the laptop sees the desktop and I'm currently transferring a couple of files.

Thanks again for the help, TheFu...I should've thought of simply reinstalling samba...had a doh! moment, which is becoming more and more common nowadays!

---

### Post by TheFu on 2013-01-03
> **mtguy said:**
> Well, curiously, after rebooting the server, all is back as it should be...even though I had restarted the samba service, my laptop couldn't see the desktop...so I figured, why not?  I rebooted the desktop and the laptop sees the desktop and I'm currently transferring a couple of files.

Thanks again for the help, TheFu...I should've thought of simply reinstalling samba...had a doh! moment, which is becoming more and more common nowadays!

We all have those.  Running thoughts passed another person is why these forums exist. I'm just glad that something I wrote was actually helpful and clicked for you. ;)

Sometimes programs and OSes cache things for us. On Linux, those usually get re-read after a reasonable time period, so reboot isn't necessary. Often a logout/login will be the most we need to do.  
On Windows, sometimes a reboot is the only way to force cached data to be dropped.

---

### Post by steeldriver on 2013-01-03
You are not going crazy - I noticed recently that after changing samba.conf (changing the WORKGROUP) on my mythbuntu box, restarting samba was NOT sufficient to propagate the change - reboot did it - maybe there are other services that also need to restart (nmbd?)

---

