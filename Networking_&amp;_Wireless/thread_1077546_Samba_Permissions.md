---
title: "Samba Permissions"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by evilspoons on 2009-02-22
Hi, I'm currently trying to make my Samba share more accessible.

I have a big blob of storage (several LVM'd hard drives) that I want everyone on the network to be able to read and write from Windows and Mac machines, without regard to their username (guests are ok to read/write).

So far I have accomplished this goal, using the smb.conf below:

```

[global]
        server string = chromebox samba %v
        interfaces = lo, eth0
        bind interfaces only = Yes
        security = SHARE
        log file = /var/log/samba/log.%m
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_SNDBUF=24576 SO_RCVBUF=24576
        workgroup = WORKGROUP
        os level = 35
        local master = No
        wins support = Yes
        read only = No
        hosts allow = 127.0.0.1, 192.168.1.0/24
        hosts deny = 0.0.0.0/0

[public]
        admin users = nobody
        path = /media/public
        write list = nobody
        guest ok = Yes
        create mask = 0774
        comment = Public
        directory mask = 0775
        force create mode = 0775
        force directory mode = 0775

[homes]
        comment = Home Directories
        browseable = No

```

However, the problem is - directories created by Samba seem to be getting the permissions 755, owned by nobody / nogroup.

This poses a problem, as my Ubuntu user "erik" in group "erik" cannot write to these folders (to download to the /public/ share from a bittorent program that runs all the time).

"force create mode = 0775" and "force directory mode = 0775" were recently added by me, and as far as I can tell, to no effect.

Any tips?

Thanks!

---

### Post by dmizer on 2009-02-24
Your smb.conf file is overly complicated and has a few problems. If you want global access, the share is really simple. This would probably be sufficient (important changes marked in red):
```
[global]
        server string = chromebox samba %v
        interfaces = lo, eth0
        bind interfaces only = Yes
        security = [COLOR="Red"]share[/COLOR]
        log file = /var/log/samba/log.%m
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_SNDBUF=24576 SO_RCVBUF=24576
        workgroup = WORKGROUP
        netbios name = [COLOR="Red"]YOUR-SERVER-NAME-HERE[/COLOR]
        os level = 35
        local master = No
        name resolve order = hosts wins bcast
        hosts deny = 0.0.0.0/0

[public]
        path = /media/public
        guest ok = Yes
        read only = No
        comment = Public

[homes]
        comment = Home Directories
        read only = No
        browseable = No
```
Then set your /media/public folder to world read/write:
```
sudo chmod -R 777 /media/public
```

Add erik to your samba users group:
```
sudo smbpasswd -L -a erik
sudo smbpasswd -L -e erik
```

Restart samba (or reboot the computer), and then things should work the way you want.

Notes (edit):

This ->
```
        interfaces = lo, eth0
        bind interfaces only = Yes
```
and this:
```
        hosts allow = 127.0.0.1, 192.168.1.0/24
```
do the exact same thing. There's no reason to use both.

This ->
```
        wins support = Yes
```
is only for use when your server is a domain controller over multiple subnets across multiple workgroups (which your server is clearly not).

This ->
```
        hosts deny = 0.0.0.0/0
```
is probably not necessary unless eth0 has multiple ip ranges? Not sure why you included this option so I left it in but you'll probably get better performance without it.

---

