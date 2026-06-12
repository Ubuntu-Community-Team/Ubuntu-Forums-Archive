---
title: "Disable browsing / displaying SAMBA shares to guests"
date: 2012-08-09
forum: Networking &amp; Wireless
---

### Post by hulk1st on 2012-08-09
Hi there,

I have the following problem: On Mac OS I can see all my samba shares, which I set up on a Ubuntu 12.04 machine, before entering credentials. So I click on the domain name, then on the name of the server and there I can see the name of all my shares (except for home, of course). However, I need to login to see the actual content of the share. Nevertheless I would like guests not to see my shares unless they log in. If I set browseable = no, I can neither see my shares before nor after login, so this is not a solution.

Any hints?

Security is set to user by the way...

```
[global]
    workgroup = ABC
    server string = server %h
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 10000
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    add machine script = sudo /usr/sbin/useradd -N -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
    logon script = logon.cmd
    logon path = 
    logon drive = Z:
    domain logons = Yes
    dns proxy = No
    wins server = *.*.*.*
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[homes]
    comment = Home Directories
    valid users = %S
    read only = No
    create mask = 0700
    directory mask = 0700
    browseable = No

[netlogon]
    comment = Network Logon Service
    path = /srv/samba/netlogon
    share modes = No

[public]
    comment = Public File Exchange Directory
    path = /srv/samba/public
    force group = sambauser
    read only = No
    create mask = 0770
    directory mask = 0770

```

---

### Post by hulk1st on 2012-08-09
Found it, the solution was to set ```
map to guest = Bad User
``` to ```
map to guest = never
```, although it is still not clear to me why.

If I now press log in as guest, I am beeing refused (as it should by). Obviously letting samba map wrong login attempts to the guest account does not lead to a refused login attempt although security is set to user ...

---

### Post by TheFu on 2012-08-09
```
usershare allow guests = no
```
might also work.

There are lots of settings in the /etc/samba/smb.conf file related to guests. I'm pretty certain they are well documented in the manpage.
```
man smb.conf
```
to learn all about it.

---

### Post by hulk1st on 2012-08-09
If I'm correct, ```
usershare allow guests = no
``` means something else. How I understand it, usershares are shares, which normal users can create on their own (as long as the respective priviliges have been added). This option denies users to create usershares having anonymous (guest) login, so he can create a share in his own, but only existing users can access it.

In my case, the guest login did not work either, but guests were able to get a listing of existing shares, although they were unable to access them. I'm propably wrong when I say, this might be a bug (because samba is estiblished for such a long time now), but still it does seem strange to me, that this listing of shares worked without logging in, when I set to map a bad user to a guest. The reason is, that only this way the listing worked, when I set myself to a guest manually, I am unable to see any shares.

Best,
hulk1st

---

### Post by Morbius1 on 2012-08-09
Just so you know that will not work for all clients under all circumstances.

"map to guest = Never" will impact a client on a Windows machine because it passes a username and password automatically by default without the user knowing it or a Linux ( and I'm guessing a Mac user ) that forces it.

If you run the following command ( with the right ip address ) on your Ubuntu machine you should see the share that you want to hide:
```
nautilus smb://192.168.0.100
```"map to guest = Bad User" will reject a user if that user is in the server's samba password database but has the wrong password. But if the client user name doesn't exist in the samba password database he is converted to the guest account and then it's up to a given share definition to determine if he can gain access.

"map to guest = Never" makes the exact same comparison to the database but if it doesn't find that user it doesn't convert the user to the guest account it just rejects him and that user isn't even allowed to view the share list.

Don't pass a username and the "map to guest" logic is never used at the browse level and that's what a Linux client does unless you force it..

---

